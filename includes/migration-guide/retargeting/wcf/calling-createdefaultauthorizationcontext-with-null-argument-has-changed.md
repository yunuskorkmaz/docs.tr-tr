### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>Null bir bağımsız değişkeni ile CreateDefaultAuthorizationContext çağırma değişti

|   |   |
|---|---|
|Ayrıntılar|Uygulaması <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=name> yapılan bir çağrı tarafından döndürülen <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=name> null authorizationPolicies ile bağımsız değişkeni, .NET Framework 4.6 uygulamasında değişti.|
|Öneri|Nadir durumlarda, özel kimlik doğrulama kullanan WCF uygulamalar davranış farklılıkları görebilirsiniz. Böyle durumlarda, önceki davranış iki yoldan biriyle geri yüklenebilir:<ol><li>.NET Framework 4.6 daha önceki bir sürümünü hedeflemek için uygulamanızın yeniden derleyin. IIS barındırılan hizmetleri için kullandığınız &lt;httpRuntime targetFramework =&quot;x.x&quot;  / &gt; .NET Framework'ün önceki bir sürümünü hedefleyecek şekilde öğesi.</li><li>Aşağıdaki satırı ekleyin <code>&lt;appSettings&gt;</code> app.config dosyasının: <code>&lt;add key=&quot;appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext&quot; value=&quot;true&quot; /&gt;</code></li></ol>|
|Kapsam|Küçük|
|Sürüm|4.6|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType></li></ul>|

