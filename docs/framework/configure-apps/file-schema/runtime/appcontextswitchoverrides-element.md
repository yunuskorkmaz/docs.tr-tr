---
title: "&lt;AppContextSwitchOverrides&gt; öğesi"
ms.custom: 
ms.date: 10/17/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ed1b11cef909af153e43d61e71a4875648bdbfb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltappcontextswitchoverridesgt-element"></a>&lt;AppContextSwitchOverrides&gt; öğesi
Tarafından kullanılan bir veya daha fazla anahtarları tanımlar <xref:System.AppContext> sınıfı yeni işlevsellik için vazgeçme mekanizma sağlar.  
  
 \<Yapılandırma >  
 \<çalışma zamanı >  
\<AppContextSwitchOverrides >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`value`|Gerekli öznitelik.<br /><br /> Bir veya daha fazla anahtar adlarını ve ilişkili Boole değerleri tanımlar.|  
  
### <a name="value-attribute"></a>Öznitelik değeri  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|"name = value"|Önceden tanımlanmış anahtar adı değerini birlikte (`true` veya `false`). Birden çok anahtar ad/değer çifti noktalı virgülle ayrılmış (";"). .NET Framework tarafından desteklenen önceden tanımlanmış anahtar adları listesi için Açıklamalar bölümüne bakın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 4.6 ile başlayan `<AppContextSwitchOverrides>` öğesi yapılandırma dosyasında Arayanların uygulama veya yeni işlevsellikten yararlanmak kitaplık önceki sürümleriyle uyumluluğunu korumak belirlemek için bir API sağlar. Örneğin, bir API'nin davranışını bir kitaplık iki sürümü arasında değişmişse `<AppContextSwitchOverrides>` öğesi arayanlar yeni işlevselliği desteklemek kitaplık sürümleri üzerinde yeni davranış dışında kabul etmek için bu API sağlar. Uygulamalar için .NET Framework API'leri çağırmak `<AppContextSwitchOverrides>` öğesi de, uygulamaları, uygulama içeren .NET Framework sürümü üzerinde çalışıyorsa, yeni işlevsellik kabul etmek için .NET Framework'ün önceki bir sürümünü hedef arayanlara izin ver işlevselliği.  
  
 `value` Özniteliği `<AppContextSwitchOverrides>` öğesi bir veya daha çok noktalı virgülle ayrılmış ad/değer çiftleri içeren tek bir dize oluşur.  Her ad uyumluluk anahtarı tanımlar ve karşılık gelen değeri olduğu bir Boole değeri (`true` veya `false`) anahtar ayarlanmış olup olmadığını gösterir. Varsayılan olarak, anahtarıdır `false`, ve kitaplıkları, yeni işlevsellik sağlar. Anahtar ayarlandıysa, yalnızca önceki işlevselliği sağladıkları (diğer bir deyişle, değeri olduğu `true`). Bu yeni işlevselliği dışında kabul etmek için önceki davranışa bağlı arayanlara izin verirken için varolan bir API yeni davranışı sağlamak kitaplıkları sağlar.  
  
 .NET Framework aşağıdaki anahtarları destekler:  
  
|Anahtar adı|Açıklama|Sunulan|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Windows Presentation Foundation denetim düzeni için eski bir algoritma kullanıp kullanmadığını denetler. Daha fazla bilgi için bkz: [azaltma: WPF düzeni](~/docs/framework/migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|  
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Ayarlandığında `false`, FIPS etkinleştirildiğinde XAML tabanlı iş akışı projelerinin Visual Studio ile hata ayıklama sağlar. Bu olmadan, bir <xref:System.NullReferenceException> System.Activities derleme yöntemlerinde çağrılarında oluşturulur.|.NET framework 4.7|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Denetimleri olup olmadığını <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> yöntemi bir özel durum oluşturur, bir <xref:System.Drawing.Icon> nesnesi PNG çerçeveler sahiptir. Daha fazla bilgi için bkz: [azaltma: simgesi nesneleri PNG çerçevelere](~/docs/framework/migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|  
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Zaman uyumsuz işlemleri çağıran iş parçacığının bağlamından geçmez olup olmadığını denetler. Daha fazla bilgi için bkz: [CurrentCulture ve CurrentUICulture akış görevleri](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Denetimleri olup olmadığını <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi, yalnızca son DNS girişi ile talep türüyle eşleşecek şekilde çalışır. Daha fazla bilgi için bkz: [azaltma: X509CertificateClaimSet.FindClaims yöntemi](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.BlockLongPaths`|Denetimleri olup olmadığını yolları daha uzun `MAX_PATH` (260 karakter) throw bir <xref:System.IO.PathTooLongException>. Daha fazla bilgi için bkz: [uzun yol Destek](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Ters eğik çizgi kullanır ("\\") yerine eğik çizgi ("/") yol ayırıcısı olarak <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> özelliği. Daha fazla bilgi için bkz: [azaltma: ZipArchiveEntry.FullName yol ayırıcısı](~/docs/framework/migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Eski yolu normalleştirme kullanılır ve tarafından desteklenen URI yolları denetleyen <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemleri. Daha fazla bilgi için bkz: [azaltma: yolu normalleştirme](~/docs/framework/migration-guide/mitigation-path-normalization.md) ve [azaltma: iki nokta üst üste yolu denetler](~/docs/framework/migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|  
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Bir test olup olmadığını eşitlik karşılaştırır için denetimleri <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> özelliği olan bir nesnenin <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> ikinci nesnesinin özelliği. Daha fazla bilgi için bkz: [MemberDescriptor.Equals yanlış uyarlamasını](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Devre dışı bırakır, Gelişmiş anahtar kullanımı (EKU) nesne tanımlayıcısı (OID) doğrulama sertifikası. Nesne tanımlayıcıları (OID) anahtarı kullanan uygulamalar belirtmek koleksiyonu bir Gelişmiş anahtar kullanımı (EKU) uzantısıdır.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|TLS1.0 tarayıcı yararlanma karşı SSL/TLS (BEAST) azaltma SCH_SEND_AUX_RECORD kullanımını devre dışı bırakarak devre dışı bırakır.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Denetimleri olup olmadığını <xref:System.Net.ServicePointManager?displayProperty=nameWithType> ve <xref:System.Net.Security.SslStream?displayProperty=nameWithType> sınıfları, SSL 3.0 protokolünü kullanabilirsiniz. Daha fazla bilgi için bkz: [azaltma: TLS protokolleri](~/docs/framework/migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|SystemDefault TLS sürümleri geri Tls12, Tls11, Tls varsayılan olarak geri alma devre dışı bırakır.|.NET framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|SslStream TLS sunucu tarafı uyarıları devre dışı bırakır.|.NET framework 4.7|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Denetimleri olup olmadığını [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) ECMAScript V6 ve V8 standartlarını temel bazı denetim karakterleri serileştirir. Daha fazla bilgi için bkz: [azaltma: DataContractJsonSerializer ile denetim karakterleri seri hale getirme](Mitigation:%20Serialization%20of%20Control%20Characters%20with%20the%20DataContractJsonSerializer.md)| .NET framework 4.7 |
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Denetimleri olup olmadığını <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> Oluşturucusu ayarlar yeni nesnenin <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> var olan bir nesne başvuruyu özelliğiyle. Daha fazla bilgi için bkz: [azaltma: Claimsıdentity Oluşturucusu](~/docs/framework/migration-guide/mitigation-claimsidentity-constructor.md).|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Denetimleri olup olmadığını yeniden denemesi bir <xref:System.Security.Cryptography.AesCryptoServiceProvider> şifre çözücü oluşturur bir <xref:System.Security.Cryptography.CryptographicException>. Daha fazla bilgi için bkz: AesCryptoServiceProvider şifre çözücü yeniden kullanılabilir transform](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform) sağlar.|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Denetimleri olup olmadığını değerini [CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) özelliği bir [IntPtr](xref:System.IntPtr) gösteren bir pencere bellek konumunu işlemek veya pencere işleyicisi (HWND) olup. Daha fazla bilgi için bkz: [azaltma: CspParameters.ParentWindowHandle bekliyor HWND](Mitigation:%20CspParameters.ParentWindowHandle%20Expects%20an%20HWND.md). |.NET framework 4.7|   
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Belirler olup olmadığını `TransportWithMessageCredential` güvenlik modu sağlar imzasız iletilerle "için" başlığı. Bu bir katılımı anahtarıdır. Daha fazla bilgi için bkz: [.NET Framework 4.6.1 çalışma zamanı değişiklikleri](https://msdn.microsoft.com/library/mt592686.aspx#WCF).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|İle X509 kullanma girişimi sertifikaları olup olmadığını CSG anahtarı depolama sağlayıcısı aykırı belirler. Daha fazla bilgi için bkz: [WCF taşıma güvenliği destekler CNG kullanarak depolanan Sertifikalar](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|İle birlikte `Switch.System.Net.DontEnableSchUseStrongCrypto`, WCF ileti güvenliğini TLS 1.1 ve TLS 1.2 kullanıp kullanmadığını belirler.|.NET framework 4.7 |    
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Windows Presentation Foundation eski bir algoritma geçerli olup olmadığını belirler (`true`) ya da yeni bir algoritma (`false`) için alan ayırma içinde \*-sütun. Daha fazla bilgi için bkz: [azaltma: kılavuz denetimin alanı ayırma yıldız sütunlara](Mitigation:%20Grid%20Control's%20Space%20Allocation%20to%20Star-columns.md). |.NET framework 4.7 |
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Özel bir veren kod dışında çevrilir <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> bir özel durum oluşturmadan iletileri güvenli bir şekilde filtrelemek için uygulama zaman <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> yöntemi çağrılır. Daha fazla bilgi için bkz: [azaltma: özel IMessageFilter.PreFilterMessage uygulamaları](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|  
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|İsteğe bağlı olup olmadığını belirleyen `WM_POINTER`-tabanlı dokunma/kalem yığını WPF uygulamalarında etkindir. Daha fazla bilgi için bkz: [azaltma: işaretçi tabanlı dokunma ve Kalem desteği](Mitigation:%20Pointer-based%20Touch%20and%20Stylus%20Support.md) | 
|`Switch.System.Windows.Media.ImageSourceConverter`<br/>`OverrideExceptionWithNullReferenceException`|Eski olup olmadığını denetler [NullReferenceException](xref:System.NullReferenceException) daha açık belirtmek gerekirse özel durumun nedeni gösteren durum yerine (gibi bir [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) veya bir [ FileNotFoundException](xref:System.IO.FileNotFoundException). İşleme üzerinde bağımlı kod tarafından kullanılması amaçlanmıştır [NullReferenceException](xref:System.NullReferenceException). | .NET framework 4.7 |
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Bileşik anahtarlar boş anahtar sıralarında XSD şema doğrulaması tarafından göz ardı edilir olup olmadığını denetler. Daha fazla bilgi için bkz: [azaltma: XML şema doğrulaması](~/docs/framework/migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|  
  
> [!NOTE]
>  Eklemek yerine bir `AppContextSwitchOverrides` öğesi bir uygulama yapılandırma dosyasını da ayarlayabilirsiniz anahtarları program aracılığıyla çağırarak `static` (C# ' ta) veya `Shared` (Visual Basic'te) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemi.  
  
 Kitaplık geliştiricilerin kendi kitaplıkları sonraki sürümlerinde sunulan değiştirilmiş işlevsellik dışında opt arayanlara izin vermek için özel anahtarlar da tanımlayabilirsiniz. Daha fazla bilgi için bkz: <xref:System.AppContext> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `AppContextSwitchOverrides` tek bir uygulama uyumluluk anahtarı tanımlamak için öğesi `Switch.System.Globalization.NoAsyncCurrentCulture`, engelleyen kültür zaman uyumsuz yöntem çağrılarını iş parçacıkları arasında akan.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 Aşağıdaki örnek kullanır `AppContextSwitchOverrides` iki uygulama uyumluluğu anahtarları tanımlamak için öğesi `Switch.System.Globalization.NoAsyncCurrentCulture` ve `Switch.System.IO.BlockLongPaths`. Noktalı virgül iki ad/değer çiftleri ayıran unutmayın.  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppContext](xref:System.AppContext?qualifyHint=False&autoUpgrade=True)  
 [\<çalışma zamanı > öğesi](runtime-element.md)  
 [\<Yapılandırma > öğesi](../configuration-element.md)
