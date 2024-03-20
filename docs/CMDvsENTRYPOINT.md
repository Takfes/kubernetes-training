## CMD vs ENTRYPOINT

### 1. `CMD` (Command)

- **Purpose**: `CMD` is used to provide defaults for an executing container. It can include an executable, or they can omit the executable, in which case you must specify an `ENTRYPOINT` instruction as well.
- **Overriding**: The `CMD` instruction can be easily overridden by specifying additional parameters at the end of `docker run`.
- **Syntax**: `CMD` can be used in three forms:
  - **Shell Form**: `CMD command param1 param2`
  - **Exec Form**: `CMD ["executable","param1","param2"]`
  - **Param Form**: `CMD ["param1","param2"]` (as parameters to `ENTRYPOINT`)
- **Use Case**: Typically used for running software contained in your image, along with any arguments.

### Example of `CMD`:

```Dockerfile
CMD ["echo", "Hello, Docker!"]
```

Or using shell form:

```Dockerfile
CMD echo "Hello, Docker!"
```

### 2. `ENTRYPOINT`

- **Purpose**: `ENTRYPOINT` allows you to configure a container that will run as an executable. It is meant to provide the executable and let you append commands as parameters.
- **Overriding**: `ENTRYPOINT` can be overridden using `docker run` with the `--entrypoint` flag.
- **Syntax**: `ENTRYPOINT` has two forms:
  - **Exec Form**: `ENTRYPOINT ["executable", "param1", "param2"]` (preferred)
  - **Shell Form**: `ENTRYPOINT command param1 param2`
- **Use Case**: Used when you want the container to be an executable and accept parameters from the `docker run` command.

### Example of `ENTRYPOINT`:

```Dockerfile
ENTRYPOINT ["echo"]
CMD ["Hello, Docker!"]
```

When you run this container, it will execute the `ENTRYPOINT` with the `CMD` as its default parameter. But you can override the `CMD` parameter.

### Key Differences:

- **Overriding Behavior**: `CMD` is easy to override, while `ENTRYPOINT` is designed to define a container’s main command and is not easily overridden.
- **Combination**: `CMD` and `ENTRYPOINT` can be used together to define a default command which can be easily overridden.
- **Use Case**: `CMD` is used to provide default arguments that can be overridden, while `ENTRYPOINT` is used to set the base command that can have arguments appended with `docker run`.

### Example of Using Both:

```Dockerfile
ENTRYPOINT ["echo"]
CMD ["Hello, Docker!"]
```

Running `docker run -it <image>` will output "Hello, Docker!", but you can override the `CMD` part: `docker run -it <image> "Hello again!"` will output "Hello again!".

In summary:

- Use `CMD` when you want to specify a default command and allow the user to easily override it.
- Use `ENTRYPOINT` when you want the container to behave exclusively as a certain executable/utility.
