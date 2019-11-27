---
title: <AppContextSwitchOverrides> Öğesi
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
ms.openlocfilehash: 34187b5fdcfcd4d08b4067213372fd12c7533cf7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430516"
---
# <a name="appcontextswitchoverrides-element"></a>\<AppContextSwitchOverrides > öğesi
Yeni işlevsellik için bir geri çevirme mekanizması sağlamak üzere <xref:System.AppContext> sınıfı tarafından kullanılan bir veya daha fazla anahtarı tanımlar.  
  
[ **\<yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<çalışma zamanı >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<AppContextSwitchOverrides >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`value`|Gerekli öznitelik.<br /><br /> Bir veya daha fazla anahtar adı ve bunlarla ilişkili Boolean değerleri tanımlar.|  
  
### <a name="value-attribute"></a>değer özniteliği  
  
|Value|Açıklama|  
|-----------|-----------------|  
|"ad = değer"|Önceden tanımlanmış bir anahtar adı ile birlikte (`true` veya `false`). Birden çok anahtar adı/değer çifti noktalı virgülle (";") ayrılır. .NET Framework tarafından desteklenen önceden tanımlanmış anahtar adlarının bir listesi için, açıklamalar bölümüne bakın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 4,6 ' den başlayarak, bir yapılandırma dosyasındaki `<AppContextSwitchOverrides>` öğesi, bir API 'nin çağıranlarının, uygulamanın yeni işlevlerden faydalanıp yararlanamayacağını veya bir kitaplığın önceki sürümleriyle uyumluluğunu koruyabilmesine izin verir. Örneğin, bir API 'nin davranışı iki bir kitaplığın sürümü arasında değiştiyse `<AppContextSwitchOverrides>` öğesi, bu API 'nin çağıranlarının yeni işlevselliği destekleyen kitaplık sürümlerindeki yeni davranışı geri almasına izin verir. .NET Framework API 'Leri çağıran uygulamalar için, `<AppContextSwitchOverrides>` öğesi, uygulamaları .NET Framework önceki bir sürümünü hedefleyen çağıranlar bu işlevselliği içeren bir .NET Framework sürümünde çalışıyorsa yeni işlevselliği kabul etmek için de izin verebilir.  
  
 `<AppContextSwitchOverrides>` öğesinin `value` özniteliği, bir veya daha fazla noktalı virgülle ayrılmış ad/değer çiftlerinden oluşan tek bir dizeden oluşur.  Her ad bir uyumluluk anahtarını tanımlar ve karşılık gelen değeri anahtarın ayarlanmış olup olmadığını belirten bir Boole (`true` veya `false`) değeridir. Varsayılan olarak, anahtar `false`ve kitaplıklar yeni işlevleri sağlar. Bunlar yalnızca, anahtar ayarlandıysa (yani, değeri `true`) önceki işlevleri sağlar. Bu, kitaplıkların var olan bir API için yeni davranış sağlamasına izin verirken önceki davranışa bağlı olan çağıranların yeni işlevselliği devre dışı vermesini sağlar.  
  
 .NET Framework aşağıdaki anahtarları destekler:  
  
|Anahtar adı|Açıklama|Dağıtıla|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Windows Presentation Foundation denetim düzeni için eski bir algoritmayı kullanıp kullanmadığını denetler. Daha fazla bilgi için bkz. [azaltma: WPF düzeni](../../../migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|PackageDigitalSignatureManager tarafından bir paketin parçalarını imzalamak için kullanılan varsayılan algoritmanın SHA1 veya SHA256 olup olmadığını denetler.<br>SHA1 ile ilgili çakışma sorunları nedeniyle Microsoft SHA256 önerir.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|`false`olarak ayarlandığında, FIPS etkin olduğunda Visual Studio ile XAML tabanlı iş akışı projelerinin hata ayıklamasına izin verir. Bu olmadan, System. Activities derlemesinde yöntemlere yapılan çağrılar halinde bir <xref:System.NullReferenceException> oluşturulur.|.NET framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Hata ayıklayıcı içindeki bir iş akışı örneği için sağlama toplamı, MD5 veya SHA1 kullanıp kullanmadığını denetler. | .NET framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|İş akışı sağlama toplamı karmasının, .NET Framework 4,7 ' de (`true`) varsayılan olarak tanıtılan SHA1 algoritmasını kullanıp kullanmadığını veya .NET Framework 4,8 ' de varsayılan olarak tanıtılan varsayılan SHA256 algoritmasını kullanıp kullanmadığını denetler (`false`).<br>SHA1 ile ilgili çakışma sorunları nedeniyle Microsoft SHA256 önerir.|.NET Framework 4,8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Taşınabilir pdb 'leri kullanırken yığın izlemelerinin elde edilip edilmeyeceğini denetler ve kaynak dosya ve satır bilgileri içerebilir. Kaynak dosya ve satır bilgilerini dahil etmek için `false`; Aksi takdirde, `true`.|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Bir <xref:System.Drawing.Icon> nesnesi PNG çerçevelerindeyken <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> yönteminin bir özel durum verip içermediğini denetler. Daha fazla bilgi için bkz. [azaltma: simge NESNELERINDE png çerçeveleri](../../../migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|<xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> yöntemi tarafından koleksiyona eklendiğinde <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> nesnelerinin düzgün şekilde atılıp atılmayacağını belirler. eski davranışı korumak için `true`; Tüm özel yazı tipi nesneleri atılırken `false`. |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|<xref:System.Windows.Forms.PrintPreviewDialog> performansının ağ yazıcıları için iyileştirilmiş olup olmadığını denetler. Daha fazla bilgi için bkz. [Printönizleme Iletişim kutusu denetimine genel bakış](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Yıl aralığının Japonca takvim için olup olmadığını denetler. yıl aralığı denetimlerini zorlamak için `true` ve devre dışı bırakmak için `false` (varsayılan davranış). Daha fazla bilgi için bkz. [takvimler Ile çalışma](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Yalnızca "1" öğesinin ayrıştırma işlemlerinde bir Japonca takvim dönemi için ilk yıl olarak tanınıp tanınmadığını denetler. yalnızca "1" öğesini tanımak `true`; "1" veya gannen (varsayılan davranış) tanınması `false`. Daha fazla bilgi için bkz. [takvimler Ile çalışma](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6| 
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Japonca takvim çağının ilk yılının, biçimlendirme işlemlerinde "1" veya gannen olarak temsil edilip edilmeyeceğini denetler. "1" olarak dönem ilk yılını biçimlendirmek için `true`; Bunu gannen olarak biçimlendirmek için `false` (varsayılan davranış). Daha fazla bilgi için bkz. [takvimler Ile çalışma](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Zaman uyumsuz işlemlerin çağıran iş parçacığının bağlamından akış yapıp yapamadığını denetler. Daha fazla bilgi için bkz. [Görevler arasında CurrentCulture ve CurrentUICulture Flow](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yönteminin yalnızca son DNS girdisiyle talep türüyle eşleştirmeye çalışıp çalışmadığını denetler. Daha fazla bilgi için bkz. [azaltma: X509CertificateClaimSet. Findclaim metodu](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|AuthorizationContext. Empty 'in kesilebilir bir nesne döndürmesini izin verip vermeyeceğinizi denetler.|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|`MAX_PATH` (260 karakter) ' den uzun yolların <xref:System.IO.PathTooLongException>oluşturmasını denetler. Daha fazla bilgi için bkz. [uzun yol desteği](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|<xref:System.IO.Compression.DeflateStream> sınıfı tarafından açma için yerel işletim sistemi yordamlarının kullanılıp kullanılmadığını denetler. Yerel API 'Leri kullanmak için `false`; <xref:System.IO.Compression.DeflateStream> uygulamasını kullanmak `true`.|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|<xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> özelliğindeki yol ayırıcısı olarak eğik çizgi ("/") yerine ters eğik çizgi ("\\") kullanır. Daha fazla bilgi için bkz. [azaltma: ZipArchiveEntry. FullName yol ayırıcısı](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|<xref:System.IO.Ports.SerialPort> akışlarıyla oluşturulan arka plan iş parçacıklarında oluşan işletim sistemi özel durumlarının işlemi sonlandırır.|.NET Framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Eski yol normalleştirme kullanılıp kullanılmadığını ve URI yollarının <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemleri tarafından desteklenip desteklenmediğini denetler. Daha fazla bilgi için bkz. [azaltma: yol normalleştirme](../../../migration-guide/mitigation-path-normalization.md) ve [azaltma: yol iki nokta denetimleri](../../../migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Bir eşitlik testinin, bir nesnenin <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> özelliğini ikinci nesnenin <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> özelliğiyle karşılaştırıp karşılaştırmayacağını denetler. Daha fazla bilgi için bkz. [MemberDescriptor. Equals Için hatalı uygulama](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Sertifika Gelişmiş anahtar kullanımı (EKU) nesne tanımlayıcısı (OID) doğrulamasını devre dışı bırakır. Gelişmiş anahtar kullanımı (EKU) uzantısı, anahtarı kullanan uygulamaları belirten bir nesne tanımlayıcıları (OID) koleksiyonudur.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|SCH_SEND_AUX_RECORD kullanımını devre dışı bırakarak SSL/TLS (BEAST) azaltma için TLS 1.0 tarayıcı açığından yararlanmaya devre dışı bırakır.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|<xref:System.Net.ServicePointManager?displayProperty=nameWithType> ve <xref:System.Net.Security.SslStream?displayProperty=nameWithType> sınıflarının SSL 3,0 protokolünü kullanıp kullanamayacağını denetler. Daha fazla bilgi için bkz. [azaltma: TLS protokolleri](../../../migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Varsayılan bir Tls12, Tls11, TLS geri dönerek SystemDefault TLS sürümlerini devre dışı bırakır.|.NET framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|SslStream TLS sunucu tarafı uyarılarını devre dışı bırakır.|.NET framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|COM birlikte çalışabilirlik olaylarında ByRef SafeArray parametrelerinin yerel koda (`false`) geri döndürülüp sıralanmadığını veya yerel koda geri hazırlanıp devre dışı bırakılıp bırakılmadığını denetler (`true`).|.NET Framework 4,8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |[DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) 'ın, ECMAScript V6 ve V8 standartlarına göre bazı denetim karakterlerini seri hale getirip getirmediğini denetler. Daha fazla bilgi için bkz [. azaltma: denetim karakterlerinin DataContractJsonSerializer Ile serileştirilmesi](../../../migration-guide/mitigation-serialization-control-characters.md)| .NET framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> birden çok ayarlamayı veya bir saat dilimi için yalnızca tek ayarlamayı destekleyip desteklemediğini denetler. `true`, tarih ve saat verilerini seri hale getirmek ve seri durumdan çıkarmak için <xref:System.TimeZoneInfo> türünü kullanır; Aksi takdirde, birden çok ayarlama kuralını desteklemeyen <xref:System.TimeZone> türünü kullanır.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|<xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> nesne serileştirme ve seri durumundan çıkarma sırasında daha büyük bir dizi boyutu kullanıp kullanmadığını denetler. Büyük nesne grafiklerinin serileştirme ve serisini kaldırma performansını <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>gibi türlere göre artırmak için bu anahtarı `true` olarak ayarlayın. |.NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|<xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> oluşturucusunun yeni nesnenin <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> özelliğini varolan bir nesne başvurusuyla mi ayarlamadığını denetler. Daha fazla bilgi için bkz. [azaltma: ClaimsIdentity Oluşturucusu](../../../migration-guide/retargeting/4.6.1-4.6.2.md).|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|<xref:System.Security.Cryptography.AesCryptoServiceProvider> bir şifre çözücü yeniden kullanma denemesinin bir <xref:System.Security.Cryptography.CryptographicException>mi olduğunu denetler. Daha fazla bilgi için bkz. [AesCryptoServiceProvider şifre çözücü yeniden kullanılabilir bir dönüşüm sağlar](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|[CspParameters. ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) özelliğinin değerinin bir pencere tanıtıcısının bellek konumunu temsil eden bir [IntPtr](xref:System.IntPtr) veya bir pencere tutamacı (bir hwnd) olup olmadığını denetler. Daha fazla bilgi için bkz [. azaltma: CspParameters. ParentWindowHandle BIR HWND bekliyor](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value). |.NET framework 4.7|   
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|FIPS modunda yönetilen şifreleme sınıflarının kullanılması <xref:System.Security.Cryptography.CryptographicException> (`true`) veya sistem kitaplıklarının (`false`) uygulanmasına bağlı olup olmadığını denetler.|.NET Framework 4,8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Bazı SignedCMS işlemleri için varsayılanın SHA1 veya SHA256 olup olmadığını belirler.<br>SHA1 ile ilgili çakışma sorunları nedeniyle Microsoft SHA256 önerir.|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|<xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType> yönteminin, işletim`false`sistemi tarafından desteklenen tüm adlandırılmış eğrileri doğru şekilde işleyeceğini denetler veya eski davranışa geri döner.|.NET Framework 4,8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Bazı SignedXML işlemleri için varsayılanın SHA1 mi yoksa SHA256 mi olduğunu belirler.<br>SHA1 ile ilgili çakışma sorunları nedeniyle Microsoft SHA256 önerir.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|`TransportWithMessageCredential` güvenlik modunun imzasız "to" üst bilgisine sahip iletilere izin verip içermediğini belirler. Bu bir kabul etme anahtarıdır. Daha fazla bilgi için bkz. [4.6.1 .NET Framework çalışma zamanı değişiklikleri](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Öğelerden biri `null`<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> oluşturucunun <xref:System.ArgumentException> oluşturulup oluşturulmayacağını denetler.|.NET Framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Bir CSG anahtar depolama sağlayıcısıyla x509 sertifikalarını kullanma denemesinin bir özel durum oluşturursa belirler. Daha fazla bilgi için bkz. [WCF Aktarım GÜVENLIĞI CNG kullanılarak depolanan sertifikaları destekler](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|Şirket içinde barındırılan bir hizmetle HTTP taşıması kullanılırken, bu değerin `true` olarak ayarlanması, WCF 'nin bir isteğin yanıt üst bilgilerine `Connection: close` üst bilgisini ekleyen bir uygulamayı yoksaymasına neden olur. Bu değerin `false` olarak ayarlanması, yanıt üst bilgilerine `Connection: close` üst bilgisinin eklenmesine olanak sağlar ve bu da yanıt gönderildikten sonra istek yuvasını kapatmaya neden olur.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Her seferinde tek bir yürütme iş parçacığına bir yer alan hizmetin örneklerinin kısıtlanması sonucunda oluşan kilitlenmeleri işler.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|`Switch.System.Net.DontEnableSchUseStrongCrypto`ile birlikte, WCF ileti güvenliğinin TLS 1,1 ve TLS 1,2 kullanıp kullanmadığını belirler.|.NET framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|`false` değeri, işletim sisteminin Protokolü seçmesini sağlamak için varsayılan yapılandırmayı ayarlar. `true` değeri, varsayılan olarak kullanılabilir en yüksek protokol olarak ayarlanır. (Önceki Framework sürümlerinin hizmet dalında de kullanılabilir)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|WCF 'de MSMQ iletileri için varsayılan ileti imzalama algoritmasının SHA1 mi yoksa SHA256 mi olduğunu belirler.<br>SHA1 ile ilgili çakışma sorunları nedeniyle Microsoft SHA256 önerir.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|WCF 'nin adlandırılmış kanallar için rastgele adlar oluşturmak üzere bir SHA1 veya SHA256 karması kullanıp kullanmadığını denetler.<br>SHA1 ile ilgili çakışma sorunları nedeniyle Microsoft SHA256 önerir.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Özel durum iletisi null olduğunda bir [NullReferenceException](xref:System.NullReferenceException) mi oluşturulup oluşturulmayacağını denetler.|.NET framework 4.7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Hizmet başlangıcında oluşturulan özel durumların <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> yönteminin çağıranına yayılıp yaymayacağını denetler.|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|<xref:System.Threading.Timer> örneklerinin, yüksek ölçekli ortamlar için performans geliştirmelerinden faydalanıp avantajına sahip olup olmadığını denetler. `true`, performans iyileştirmeleri etkinleştirilir; `false` (varsayılan değer) devre dışı bırakılır.|.NET Framework 4,8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Bazen çözülmüş olan belirli yüzde kodlamalı karakterlerin artık tutarlı bir şekilde kodlanmış olduğunu belirler. `true`, bunlar kodu çözülür; Aksi takdirde, `false`.|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|URI 'Lerinde Unicode çift yönlü karakterlerin işlenmesini belirler. Bunları URI 'lerden şeridi için `true`; bunları korumak ve onları yüzde olarak kodlamak `false`.|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Windows Presentation Foundation, \*sütunlara alan ayırmak için eski bir algoritma (`true`) veya yeni bir algoritma (`false`) uygulanıp uygulanmadığını belirler. Daha fazla bilgi için bkz. [azaltma: Grid denetiminin boşluk tahsisi Için yıldız-sütun](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns). |.NET framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Seçim değiştirilen olayı oluşturmadan önce bir seçicinin veya sekme denetiminin her zaman seçili değer özelliğinin değerini güncelleştirip güncelleştirmediğini denetler.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|<xref:System.Windows.Controls.TextBox> için donatıcı tabanlı seçim işlemenin kullanılıp kullanılamayacağını ve <xref:System.Windows.Controls.PasswordBox> denetimleri (`false`) veya metnin yalnızca donatıcı katmanında işlenip işlenmeyeceğini (`true`) belirler.|.NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Özel IList dizin oluşturucularının, <xref:System.Windows.Data.Binding?displayProperty=nameWithType> sınıfı tarafından yanlış şekilde (`true`) veya doğru şekilde (`false`) kullanılıp kullanılmadığını denetler.|.NET Framework 4,8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|DPı değişikliklerinin sistem başına mi (`false`değeri) yoksa izleyici temelinde mi (bir `true`değeri) olacağını belirler.|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|WPF, izleyici ile uyumlu modda çalıştırıldığında <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> denetimlerinin boyutlandırılmasına yönelik iyileştirmelerin devre dışı bırakılıp bırakılmadığını denetler (`true`) veya etkin (`false`).|.NET Framework 4,8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Denetim metni mevcut olduğunda geliştiricinin <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> eylemini özel olarak işlemesini isteyip istemediğinizi belirler. <xref:System.Windows.Forms.DomainUpDown.UpButton> eylemini işlemek için `true`; <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> eylemlerinin `false` düzgün şekilde eşitlenmesi.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Özel bir <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulamasına, <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> yöntemi çağrıldığında özel bir durum oluşturmadan iletileri güvenli bir şekilde filtrelemesine olanak tanıyan kodun dışına çıkma. Daha fazla bilgi için bkz. [azaltma: Custom IMessageFilter. PreFilterMessage uygulamaları](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|  
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Kullanıcı menüyü iç içe bir <xref:System.Windows.Forms.ToolStripMenuItem> denetiminden açtığında <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> özelliğinin kaynak denetimi döndürüp döndürmeyeceğini belirler. eski davranışı `null`döndürmek için `true`; kaynak denetimini döndürmek için `false`.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Araç ipucu çağırma desteğinin devre dışı olup olmadığını denetler (`true`) veya etkin (`false`). Araç ipucu çağırma desteğini etkinleştirmek, `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`ve `Switch.UseLegacyAccessibilityFeatures.3` tümünün devre dışı bırakılması (`false`olarak ayarlanır) tarafından tanımlanan eski erişilebilirlik özelliklerini de gerektirir.|.NET Framework 4,8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|WPF uygulamalarında isteğe bağlı `WM_POINTER`tabanlı bir dokunmatik/Stilus yığınının etkinleştirilip etkinleştirilmediğini belirler. Daha fazla bilgi için bkz [. azaltma: işaretçi tabanlı dokunmatik ve ekran kalemi desteği](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Sağlama toplamı için kullanılan varsayılan karma algoritmanın SHA256 (`false`) veya SHA1 (`true`) olup olmadığını belirler.<br>SHA1 ile ilgili çakışma sorunları nedeniyle Microsoft SHA256 önerir.|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Özel durumun nedenini (bir [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) veya bir [FileNotFoundException](xref:System.IO.FileNotFoundException)gibi) daha özel olarak belirten özel durum yerine eski bir [NullReferenceException](xref:System.NullReferenceException) olup olmadığını denetler. [NullReferenceException](xref:System.NullReferenceException)öğesinin işlenmesine bağlı olan kod tarafından kullanılmak üzere tasarlanmıştır. | .NET framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|İş akışı proje Derlemeleriyle XOML dosyalarının sağlama toplamı karmasının, MD5 algoritmasını (`true`) mi yoksa .NET Framework 4,8 ' de varsayılan olarak tanıtılan SHA256 algoritmasını kullanıp kullanmadığını denetler.<br>MD5 ile ilgili çarpışma sorunları nedeniyle Microsoft SHA256 önerir.|.NET Framework 4,8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|SqlTrackingService tarafından sağlanan sağlama toplamı karmasının, önbelleğe alınmış dizeler için MD5 algoritmasını (`true`) kullanıp kullanmadığını veya .NET Framework 4,8 ' de varsayılan olarak tanıtılan SHA256 algoritmasını kullanıp kullanmadığını denetler.<br>MD5 ile ilgili çarpışma sorunları nedeniyle Microsoft SHA256 önerir.|.NET Framework 4,8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Iş akışı çalışma zamanı tarafından sağlanan sağlama toplamı karmasının, önbelleğe alınmış iş akışı tanımları için MD5 algoritmasını (`true`) kullanıp kullanmadığını veya .NET Framework 4,8 ' de varsayılan olarak tanıtılan SHA256 algoritmasını kullanıp kullanmadığını denetler.<br>MD5 ile ilgili çarpışma sorunları nedeniyle Microsoft SHA256 önerir.|.NET Framework 4,8|
|`Switch.UseLegacyAccessibilityFeatures`|.NET Framework 4.7.1 ile başlayan erişilebilirlik özelliklerinin etkin veya devre dışı olup olmadığını denetler. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|.NET Framework 4.7.2 ' de kullanılabilir erişilebilirlik özelliklerinin etkinleştirilip etkinleştirilmediğini denetler (`false`) veya devre dışı (`true`). `true`, .NET Framework 4.7.1 erişilebilirlik özelliklerini etkinleştirmek için `Switch.UseLegacyAccessibilityFeatures` de `true` olmalıdır.|.NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|.NET Framework 4,8 ' de sunulan erişilebilirlik özelliklerinin etkinleştirilip etkinleştirilmediğini denetler (`false`) veya devre dışı (`true`). `true`, `Switch.UseLegacyAccessibilityFeatures` ve `Switch.UseLegacyAccessibilityFeatures.2` de `true`olmalıdır.|.NET Framework 4,8|
|`Switch.UseLegacyToolTipDisplay`|Bir Kullanıcı fare imlecini bir WPF denetimi (`true`) üzerinde gezdirildiğinde araç ipuçlarının görüntülenip görüntülenmeyeceğini veya hem klavye odağında hem de klavye kısayol tuşu aracılığıyla (`false`, varsayılan davranış) görüntülenip görüntülenmeyeceklerini denetler. .NET Framework 4,8 üzerinde çalışan ancak .NET Framework önceki sürümlerini hedefleyen uygulamalar için hem klavye odağının hem de kısayol tuşu desteğini etkinleştirmek, `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`ve `Switch.UseLegacyAccessibilityFeatures.3` tümünün `false`olarak ayarlanmasını gerektirir.|.NET Framework 4,8|
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Bileşik anahtarlarda boş anahtar sıralarının XSD şema doğrulaması tarafından yoksayılıp yoksayılmadığını denetler. Daha fazla bilgi için bkz. [azaltma: XML şema doğrulaması](../../../migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|  
  
> [!NOTE]
> Uygulama yapılandırma dosyasına bir `AppContextSwitchOverrides` öğesi eklemek yerine, `static` (içinde C#) veya `Shared` (Visual Basic olarak) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemini çağırarak, anahtarları program aracılığıyla da ayarlayabilirsiniz.  
  
 Kitaplık geliştiricileri, arayanların, kitaplıklarının sonraki sürümlerinde tanıtılan değiştirilmiş işlevselliği devre dışı yapmasına izin vermek için özel anahtarlar da tanımlayabilir. Daha fazla bilgi için <xref:System.AppContext> sınıfına bakın.  
  
## <a name="switches-in-aspnet-applications"></a>ASP.NET uygulamalarındaki anahtarlar

Web. config dosyasının [\<appSettings >](../appsettings/index.md) bölümüne bir [\<Add >](../appsettings/add-element-for-appsettings.md) öğesi ekleyerek uyumluluk ayarlarını kullanmak üzere bir ASP.NET uygulamasını yapılandırabilirsiniz. 

Aşağıdaki örnek, Web. config dosyasının `<appSettings>` bölümüne iki ayar eklemek için `<add>` öğesini kullanır:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `Switch.System.Globalization.NoAsyncCurrentCulture`tek bir uygulama uyumluluk anahtarı tanımlamak için `AppContextSwitchOverrides` öğesini kullanır, bu, kültürün zaman uyumsuz yöntem çağrılarında iş parçacıkları arasında akmasını önler.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 Aşağıdaki örnek, `Switch.System.Globalization.NoAsyncCurrentCulture` ve `Switch.System.IO.BlockLongPaths`iki uygulama uyumluluk anahtarı tanımlamak için `AppContextSwitchOverrides` öğesini kullanır. Noktalı virgülle iki ad/değer çiftini ayırır.  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppContext?displayProperty=nameWithType>
- [\<Runtime > öğesi](runtime-element.md)
- [\<Yapılandırma > öğesi](../configuration-element.md)
