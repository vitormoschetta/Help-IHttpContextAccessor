# Help-IHttpContextAccessor

IHttpContextAccessor é uma classe de extensão para HttpContext, para gerenciar Sessions e Usuários do Identity.

#### CONFIGURAR STARTUP
Adicionar no método _ConfigureServices_:
```
services.AddHttpContextAccessor();
```

#### Repositorio:
```
public class ProdutoRepositorio
{
	private readonly IHttpContextAccessor _httpContextAccessor;
 	public BaseEletronicaRepository(IHttpContextAccessor httpContextAccessor)
	{
		_httpContextAccessor = httpContextAccessor;
	}
  
  public void UsuarioLogado()
  {
      var usuario = _httpContextAccessor.HttpContext.User.Identity.Name
  }
	
  public void GravarSession()
  {
      _httpContextAccessor.HttpContext.Session.SetString("NomeSession", "valorSession");
  }
	
	public void BuscarSession()
  {
      var valorSession = _httpContextAccessor.HttpContext.Session.GetString("NomeSession");
  }
	
	public void LimparSession()
  {
      _httpContextAccessor.HttpContext.Session.Remove("NomeSession");
  }
}
```
