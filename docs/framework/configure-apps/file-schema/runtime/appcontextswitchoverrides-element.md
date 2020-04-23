---
title: AppContextSwitchOverrides Öğesi
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
ms.openlocfilehash: 8d5cd73bb9393533cb669581420e24297cb5ff71
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102937"
---
# <a name="appcontextswitchoverrides-element"></a>\<AppContextSwitchOverrides> öğesi

<xref:System.AppContext> Yeni işlevler için bir devre dışı bırakma mekanizması sağlamak için sınıf tarafından kullanılan bir veya daha fazla anahtarı tanımlar.

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<AppContextSwitchOverrides>**

## <a name="syntax"></a>Sözdizimi

```xml
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`value`|Gerekli öznitelik.<br /><br /> Bir veya daha fazla anahtar adlarını ve bunların ilişkili Boolean değerlerini tanımlar.|

### <a name="value-attribute"></a>değer Özniteliği

|Değer|Açıklama|
|-----------|-----------------|
|"ad=değer"|Değeri`true` (veya) `false`ile birlikte önceden tanımlanmış bir anahtar adı. Birden çok anahtar adı/değer çiftleri yarı iki nokta üst üste (";") ayrılır. .NET Framework tarafından desteklenen önceden tanımlanmış anahtar adlarının listesi için Açıklamalar bölümüne bakın.|

### <a name="child-elements"></a>Alt Öğeler
 Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar
 .NET Framework 4.6 ile `<AppContextSwitchOverrides>` başlayarak, yapılandırma dosyasındaki öğe, API'yi arayanların uygulamalarının yeni işlevlerden yararlanıp yararlanamayacağını veya kitaplığın önceki sürümleriyle uyumluluğu koruyup koruyamayacağını belirlemelerine olanak tanır. Örneğin, bir API'nin davranışı kitaplığın iki sürümü arasında `<AppContextSwitchOverrides>` değiştiyse, öğe, bu API'yi arayanların kitaplığın yeni işlevselliği destekleyen sürümlerindeki yeni davranışı devre dışı bırakmalarına olanak tanır. .NET Framework'de API'leri çağıran `<AppContextSwitchOverrides>` uygulamalar için öğe, uygulamaları .NET Framework'ün önceki bir sürümünü hedefleyen arayanların, uygulamaları bu işlevselliği içeren .NET Framework'ün bir sürümünde çalışıyorsa yeni işlevselliği etkinleştirmelerine de izin verebilir.

 Öğenin `value` `<AppContextSwitchOverrides>` özniteliği, bir veya daha fazla yarı sütunlu ad/değer çiftlerinden oluşan tek bir dizeden oluşur.  Her ad bir uyumluluk anahtarı tanımlar ve karşılık gelen`true` `false`değeri anahtarın ayarlanıp ayarlanmadığını gösteren bir Boolean (veya) değeridir. Varsayılan olarak, anahtar `false`ve kitaplıklar yeni işlevselliği sağlar. Yalnızca anahtar ayarlanmışsa (yani değeri) önceki işlevselliği `true`sağlarlar. Bu, kitaplıkların varolan bir API için yeni davranış sağlamasına olanak sağlarken, önceki davranışa bağlı olan arayanların yeni işlevselliği devre dışı bırakmalarına olanak tanır.

.NET Framework aşağıdaki anahtarları destekler:

|Anahtar adı|Açıklama|Tanıttı|
|-----------------|-----------------|----------------|
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Windows Sunu Temel'in denetim düzeni için eski bir algoritma kullanıp kullanmadığını denetler. Daha fazla bilgi için [azaltma: WPF Düzeni'](../../../migration-guide/mitigation-wpf-layout.md)ne bakın.|.NET Framework 4.6|
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|PackageDigitalSignatureManager tarafından bir paketin parçalarını imzalamak için kullanılan varsayılan algoritmanın SHA1 veya SHA256 olup olmadığını denetler.<br>SHA1 ile çakışan sorunlar nedeniyle, Microsoft SHA256 önerir.|.NET Çerçeve 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|`false`Ayarlandığında, FIPS etkinleştirildiğinde Visual Studio ile XAML tabanlı iş akışı projelerinin hata ayıklanmasına izin verir. Bu olmadan, <xref:System.NullReferenceException> System.Activities derlemesindeki metotlara çağrılar atılır.| .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Hata ayıklayıcıdaki iş akışı örneği için denetim umumun MD5 veya SHA1 kullanıp kullanmadığını denetler. |  .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|İş akışı denetimi karma karma ,NET Framework 4.7 (),`true`temerrüt olarak tanıtılan SHA1 algoritmasını mı yoksa .NET Framework 4.8'de`false`varsayılan olarak tanıtılan varsayılan SHA256 algoritmasını kullanıp kullanmadığını denetler.<br>SHA1 ile çakışan sorunlar nedeniyle, Microsoft SHA256 önerir.| .NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Taşınabilir PDB'ler kullanırken yığın izlerinin elde edilip edilemeyeceğini denetler kaynak dosyası ve satır bilgileri içerir. `false`kaynak dosya ve satır bilgilerini eklemek için; aksi `true`takdirde, .| .NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Bir <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> <xref:System.Drawing.Icon> nesnePNG çerçeveleri olduğunda yöntemin özel durum atıp atmadığını denetler. Daha fazla bilgi için [bkz: Simge Nesnelerinde PNG Çerçeveler.](../../../migration-guide/mitigation-png-frames-in-icon-objects.md)|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Yöntemle <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> koleksiyona eklendiğinde nesnelerin düzgün bir şekilde atılıp atılmadığını belirler. <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> `true`eski davranışı sürdürmek için; `false` tüm özel yazı tipi nesnelerini elden çıkarmak için. | .NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Ağ yazıcıları için <xref:System.Windows.Forms.PrintPreviewDialog> performansın optimize edilip edilemeyeceğini denetler. Daha fazla bilgi için [PrintPreviewDialog denetimine genel bakış](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md)alameti dir.|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Japonca takvim dönemlerinin yıl aralığı denetimlerinin uygulanıp uygulanmadığını denetler. `true`yıl aralığı denetimleri `false` zorlamak ve bunları devre dışı (varsayılan davranış). Daha fazla bilgi için [bkz.](../../../../standard/datetime/working-with-calendars.md)|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Ayrıştırma işlemlerinde yalnızca "1"in Japonca takvim döneminin ilk yılı olarak kabul edilip edilemeyeceğini denetler. `true`sadece "1"i tanımak için; `false` "1" veya Gannen 'ı (varsayılan davranış) tanımak için. Daha fazla bilgi için [bkz.](../../../../standard/datetime/working-with-calendars.md)|.NET Framework 4.6|
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Bir Japon takvim döneminin ilk yılının biçimlendirme işlemlerinde "1" veya Gannen olarak temsil edilip edilemeyeceğini denetler. `true`dönemin ilk yılını "1" olarak biçimlendirmek için; `false` Gannen (varsayılan davranış) olarak biçimlendirmek için. Daha fazla bilgi için [bkz.](../../../../standard/datetime/working-with-calendars.md)|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Adinanöz işlemlerin çağrı iş parçacığının bağlamından akıp akmadığını denetler. Daha fazla bilgi [için, görevler arasında CurrentCulture ve CurrentUICulture akışına](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks)bakın.|.NET Framework 4.6|
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Yöntemin <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> talep türünü yalnızca son DNS girişiyle eşleştirmeye çalışıp çalışılmadığını denetler. Daha fazla bilgi için, [Azaltma bakın: X509CertificateClaimSet.FindClaims Yöntemi](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Yetki Bağlamı.Boş'un mutable nesnedöndürmesine izin verip vermeyeceğine denetler.|.NET Framework 4.6|
|`Switch.System.IO.BlockLongPaths`|Yolların (260 karakter) daha `MAX_PATH` uzun <xref:System.IO.PathTooLongException>olup olmadığını denetler. Daha fazla bilgi için [Uzun Yol Desteği'ne](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support)bakın.|.NET Framework 4.6.2|
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Yerel işletim sistemi yordamlarının sınıf tarafından <xref:System.IO.Compression.DeflateStream> dekompresyon için kullanılıp kullanılmayacağını denetler. `false`yerel API'leri kullanmak için; `true` uygulamasını kullanmak <xref:System.IO.Compression.DeflateStream> için.| .NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Özellikteki yol ayırıcısı olarak ileri eğik çizgi ("/") yerine ters eğik çizgiyi ("\\") kullanır. <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> Daha fazla bilgi için [bkz: ZipArchiveEntry.FullName Yol Ayırıcı](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|<xref:System.IO.Ports.SerialPort> Akışlarla oluşturulan arka plan iş parçacıklarına atılan işletim sistemi özel durumlarının işlemi sonlandırıp sonlandırmadığını denetler.|.NET Çerçeve 4.7.1|
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Eski yol normalleştirmenin kullanılıp kullanılmadığını ve <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> URI <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yollarının ve yöntemlerle desteklenip desteklenmediğini denetler. Daha fazla bilgi için [bkz: Azaltma: Yol Normalleştirme](../../../migration-guide/mitigation-path-normalization.md) ve [Azaltma: Yol İkinokta Üst Üste Denetimleri](../../../migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Eşitlik için bir testin bir <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> nesnenin özelliğini <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> ikinci nesnenin özelliğiyle karşılaştırıp karşılaştırmadığını denetler. Daha fazla bilgi için [Üye Tanımlayıcı.Equals'ın yanlış uygulanmasına](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals)bakın.|.NET Framework 4.6.2|
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Devre dışı bırakma sertifikası gelişmiş anahtar kullanımı (EKU) nesne tanımlayıcısı (OID) doğrulaması. Gelişmiş anahtar kullanımı (EKU) uzantısı, anahtarı kullanan uygulamaları gösteren nesne tanımlayıcıları (OSB) koleksiyonudur.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|SCH_SEND_AUX_RECORD kullanımını devre dışı bırakarak TLS1.0 Tarayıcı Exploit Against SSL/TLS (BEAST) azaltıcı devre dışı bırakma.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|<xref:System.Net.Security.SslStream?displayProperty=nameWithType> Sınıfların <xref:System.Net.ServicePointManager?displayProperty=nameWithType> SSL 3.0 protokolünü kullanıp kullanamayacağını denetler. Daha fazla bilgi için [bkz: Azaltma: TLS Protokolleri.](../../../migration-guide/mitigation-tls-protocols.md)|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Devre Dışı Bırakma SistemiVarsayılan TLS sürümleri tls12, Tls11, Tls varsayılanına geri döner.| .NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|SslStream TLS sunucu tarafındaki uyarıları devre dışı kılabilir.| .NET Framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|COM interop olaylarındaki ByRef SafeArray parametrelerinin`false`yerel koda geri dönüp dönmeyeceğini`true`veya yerel koda geri dönmenin devre dışı bırakıldığını denetler ( ).| .NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |[DataContractJsonSerializer'ın](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) ECMAScript V6 ve V8 standartlarına göre bazı denetim karakterlerini serihale getirip getirmeyeceğini denetler. Daha fazla bilgi için [bkz: Azaltma: DataContractJsonSerializer ile Kontrol Karakterleri Serileştirme](../../../migration-guide/mitigation-serialization-control-characters.md)|  .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Birden çok <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ayarlamayı mı yoksa saat dilimi için yalnızca tek bir ayarlamayı mı destekler. `true`Tarih ve saat <xref:System.TimeZoneInfo> verilerini serihale getirmek ve deserialize etmek için türü kullanıyorsa; aksi takdirde, <xref:System.TimeZone> birden çok ayarlama kuralını desteklemeyen türü kullanır.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|Nesne <xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> serileştirme ve deserialization sırasında daha büyük bir dizi boyutu kullanıp kullanmayacağını denetler. Bu anahtarı, `true` büyük nesne grafiklerinin serileştirme ve deserialization performansını artırmak <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>için ayarlayın. | .NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Oluşturucu, <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29> yeni nesnenin <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> özelliğini varolan bir nesne başvurusuyla ayarlayıp ayarlamadığını denetler. Daha fazla bilgi için [bkz: Azaltma: ClaimsIdentity Constructor](../../../migration-guide/retargeting/4.6.1-4.6.2.md).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|<xref:System.Security.Cryptography.AesCryptoServiceProvider> Şifre çözücünün yeniden kullanılmaya çalışıp çalışmadığını <xref:System.Security.Cryptography.CryptographicException>denetler. Daha fazla bilgi için, [AesCryptoServiceProvider şifre çözücü](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform)yeniden kullanılabilir bir dönüşüm sağlar bakın.|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|[CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) özelliğinin değerinin bir pencere tanıtıcısının bellek konumunu temsil eden bir [IntPtr](xref:System.IntPtr) mı yoksa pencere tutamacı mı (HWND) olduğunu denetler. Daha fazla bilgi için [bkz: Azaltma: CspParameters.ParentWindowHandle bir HWND bekliyor.](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value) | .NET Framework 4.7|
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|FIPS modunda yönetilen şifreleme sınıflarının kullanımının a <xref:System.Security.Cryptography.CryptographicException> `true`( ) veya sistem kitaplıklarının`false`uygulanmasına bağlı olup olmadığını denetler.| .NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Bazı İmzaCMS işlemleri için varsayılan ıN SHA1 mi yoksa SHA256 mı olduğunu belirler.<br>SHA1 ile çakışan sorunlar nedeniyle, Microsoft SHA256 önerir.|.NET Çerçeve 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|Yöntemin <xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType> işletim sistemi tarafından desteklenen tüm adlandırılmış eğrileri doğru`false`şekilde işleyip işlemediğini veya eski davranışa geri döndürülüp döndürülmediğini denetler.| .NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Bazı İmzaXML işlemleri için varsayılan ıN SHA1 mi yoksa SHA256 mı olduğunu belirler.<br>SHA1 ile çakışan sorunlar nedeniyle, Microsoft SHA256 önerir.|.NET Çerçeve 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Güvenlik modunun `TransportWithMessageCredential` imzasız "için" üstbilgiiçeren iletilere izin verip vermeyemeyeceğini belirler. Bu bir tercih anahtarıdır. Daha fazla bilgi için [,.NET Framework 4.6.1'deki Çalışma Süresi Değişiklikleri'ne](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf)bakın.|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Yapı oluşturucunun <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> bir <xref:System.ArgumentException> öğe yi atıp `null`atmadığını denetler.|.NET Çerçeve 4.7.1|
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|CSG anahtar depolama sağlayıcısıyla X509 sertifikalarını kullanma girişiminin bir özel durum açıp açmayacağını belirler. Daha fazla bilgi için [WCF aktarım güvenlik destekleri cng kullanılarak depolanan bakın.](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng)|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|HTTP aktarımını kendi barındırılan bir hizmetle `true` kullanırken, bu değeri `Connection: close` WCF'nin bir istek için yanıt üstbilgisine üstbilgi ekleyen bir uygulamayı yok sayması için ayarlamak. Yanıt `false` `Connection: close` üstbilgisine üstbilgi eklenmesini sağlayacak şekilde bu değeri ayarlamak, yanıt gönderildikten sonra istek yuvasının kapatılmasıyla sonuçlanır.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Yeniden giren bir hizmetin örneklerini bir defada tek bir yürütme iş parçacığıyla sınırlandıran kilitlenmeleri işler.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Bununla `Switch.System.Net.DontEnableSchUseStrongCrypto`birlikte, WCF ileti güvenliğinin TLS 1.1 ve TLS 1.2 kullanıp kullanmadığını belirler.| .NET Framework 4.7 |
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|İşletim `false` sisteminin protokolü seçmesine izin vermek için varsayılan yapılandırmayı ayarlar. Varsayılan değeri `true` kullanılabilir en yüksek iletişim kuralına ayarlar. (Önceki çerçeve sürümlerinin servis dalında da mevcuttur)|.NET Çerçeve 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|WCF'deki MSMQ iletileri için varsayılan ileti imzalama algoritmasının SHA1 mi yoksa SHA256 mı olduğunu belirler.<br>SHA1 ile çakışan sorunlar nedeniyle, Microsoft SHA256 önerir.|.NET Çerçeve 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|WCF'nin adlandırılmış borular için rasgele adlar oluşturmak için SHA1 veya SHA256 karma kullanıp kullanmadığını denetler.<br>SHA1 ile çakışan sorunlar nedeniyle, Microsoft SHA256 önerir.|.NET Çerçeve 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Özel durum iletisi null olduğunda [NullReferenceException](xref:System.NullReferenceException) atılıp atılmayacağıdenetlenir.| .NET Framework 4.7|
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Hizmet başlatmada atılan özel durumların <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> yöntemin arayana yayılıp yayılmadığını denetler.|.NET Çerçeve 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|Örneklerin <xref:System.Threading.Timer> yüksek ölçekli ortamlar için performans iyileştirmelerinden yararlanıp yararlanmadığını denetler. `true`Performans iyileştirmeleri etkinse; (varsayılan değer) varsa, `false` devre dışı bırakılır.| .NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Bazen kodlanmış belirli yüzde kodlanmış karakterlerin artık sürekli olarak kodlanıp kodlanmayacağını belirler. Eğer, `true`bunlar deşifre edilirse; aksi `false`takdirde, .| .NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Urii'lerde Unicode çift yönlü karakterlerin işlenmesini belirler. `true`URI'lerden onları soymak için; `false` korumak ve yüzde-kodlamak için.| .NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Windows Presentation Foundation'ın`true``false` \*-sütunlara alan ayırmada eski bir algoritma () veya yeni bir algoritma () kullanıp uygulamadığını belirler. Daha fazla bilgi için [bkz: Azaltma: Izgara Denetimi'nin Yıldız sütunlarına Alan Tahsisi.](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns) | .NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Seçicinin veya sekme denetiminin, değiştirilen seçimi yükseltmeden önce seçili değer özelliğinin değerini her zaman güncelleştirip güncellemediğini denetler.|.NET Çerçeve 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|<xref:System.Windows.Controls.TextBox> Tıkanmış metni önlemek <xref:System.Windows.Controls.PasswordBox> `false`için Adorner tabanlı olmayan seçim oluşturmanın kullanılabilir olup olmadığını ve denetimlerin kullanılabilir olup olmadığını veya`true`metnin yalnızca Adorner katmanında işlenip işlenmediğini belirler ( ).| .NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Özel IList dizinleyicilerinin`true``false` <xref:System.Windows.Data.Binding?displayProperty=nameWithType> sınıf tarafından yanlış () veya doğru ( ) kullanılıp kullanılmadığını denetler.| .NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|DPI değişikliklerinin sistem başına (bir `false`değer) veya monitör başına (bir değer) `true`gerçekleşip gerçekleşmediğini belirler.|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|WPF monitör başına farkında modunda <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> çalıştırıldığında denetimlerin boyutlandırılmasındaki gelişmelerin devre`true`dışı bırakıldığını veya etkinleştirilip etkinleştirilmediğini denetler.`false`| .NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Denetim metni bulunduğunda geliştiricinin <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> eylemi özel olarak işlemesi gerekip gerekmediğini belirler. `true`<xref:System.Windows.Forms.DomainUpDown.UpButton> eylemi işlemek için; `false` <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> eylemlerin düzgün bir şekilde senkronize olması için.| .NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> Yöntem çağrıldığında özel <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> bir uygulamanın iletileri özel bir özel durum atmadan güvenli bir şekilde filtrelemesine olanak tanıyan kodu devre dışı bırakmaz. Daha fazla bilgi için [bkz: Azaltma: Özel IMessageFilter.PreFilterMessage Uygulamaları.](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)|.NET Framework 4.6.1|
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Kullanıcı iç <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> içe olan <xref:System.Windows.Forms.ToolStripMenuItem> denetimden menüyü açtığında özelliğin kaynak denetimini döndürüp döndürmeyeceğini belirler. `true`dönmek `null`için , eski davranış; `false` kaynak denetimini döndürmek için.| .NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Araç ipucu çağırma desteğinin devre`true`dışı bırakıldığını veya etkin olup olmadığını denetler .`false` Araç ipucu çağırma desteğini `Switch.UseLegacyAccessibilityFeatures`etkinleştirmek, ", " `Switch.UseLegacyAccessibilityFeatures.2`tarafından `Switch.UseLegacyAccessibilityFeatures.3` tanımlanan eski erişilebilirlik `false`özellikleri de gerektirir ve tüm bunlar devre dışı bırakılmalıdır (ayarlanacak).| .NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|WPF uygulamalarında `WM_POINTER`isteğe bağlı tabanlı dokunma/stylus yığınının etkin olup olmadığını belirler. Daha fazla bilgi için [azaltma: Pointer tabanlı Dokunma ve Stylus Desteği](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)| .NET Framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Checksums için kullanılan varsayılan karma algoritmasının SHA256`false`( )`true`veya SHA1 ( olup olmadığını belirler.<br>SHA1 ile çakışan sorunlar nedeniyle, Microsoft SHA256 önerir.| .NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Özel durum [(DizinNotFoundException](xref:System.IO.DirectoryNotFoundException) veya [FileNotFoundException](xref:System.IO.FileNotFoundException)gibi) nedenlerini özel olarak gösteren özel durum yerine eski bir [NullReferenceException](xref:System.NullReferenceException) atılıp atılmadığını denetler. [NullReferenceException](xref:System.NullReferenceException)işleme bağlıdır kod tarafından kullanılmak üzere tasarlanmıştır. |  .NET Framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|İş akışı projesi nde XOML dosyalarının checksum karma sının MD5`true`algoritmasını () kullanıp kullanmadığını veya .NET Framework 4.8'de varsayılan olarak tanıtılan SHA256 algoritmasını kullanıp kullanmadıklarını denetler.<br>MD5 ile çakışan sorunlar nedeniyle, Microsoft SHA256 önerir.| .NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|SqlTrackingService tarafından checksum karma önbelleğe alınmış dizeleri için MD5 algoritması ( )`true`veya .NET Framework 4.8 varsayılan olarak tanıtılan SHA256 algoritması kullanır olup olmadığını denetler.<br>MD5 ile çakışan sorunlar nedeniyle, Microsoft SHA256 önerir.| .NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|İş Akışı Runtime tarafından checksum karma önbelleğe alınmış`true`iş akışı tanımları için MD5 algoritması () kullanır veya .NET Framework 4.8 varsayılan olarak tanıtılan SHA256 algoritması kullanır olup olmadığını denetler.<br>MD5 ile çakışan sorunlar nedeniyle, Microsoft SHA256 önerir.| .NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|.NET Framework 4.7.1'den başlayarak kullanılabilir erişilebilirlik özelliklerinin etkin veya devre dışı olup olmadığını denetler. | .NET Çerçeve 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|.NET Framework 4.7.2'de bulunan erişilebilirlik özelliklerinin etkin`false``true`mi yoksa devre dışı mı olduğunu denetler. Eğer `true` `Switch.UseLegacyAccessibilityFeatures` , aynı `true` zamanda .NET Framework 4.7.1 erişilebilirlik özelliklerini etkinleştirmek gerekir.| .NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|.NET Framework 4.8'de tanıtılan erişilebilirlik özelliklerinin etkin`false``true`mi yoksa devre dışı mı olduğunu denetler. Eğer `true` `Switch.UseLegacyAccessibilityFeatures` , `Switch.UseLegacyAccessibilityFeatures.2` ve `true`aynı zamanda olmalıdır .| .NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|Bir kullanıcı fare imlecini WPF denetiminin üzerinde gezdirdiğinde araç`true`uçlarının görüntülenip görüntülenmediğini veya hem klavye odağında hem de klavye kısayol tuşu (varsayılan`false`davranış) aracılığıyla görüntülenip görüntülenmediğini denetler. .NET Framework 4.8 üzerinde çalışan ancak .NET Framework'ün önceki sürümlerini hedefleyen uygulamalar için, `Switch.UseLegacyAccessibilityFeatures`hem `Switch.UseLegacyAccessibilityFeatures.2`klavye `Switch.UseLegacyAccessibilityFeatures.3` odağı hem `false`de kısayol tuşu desteğini etkinleştirmek için , ve tüm .| .NET Framework 4.8|
|`Switch.System.Xml.`<br />`IgnoreEmptyKeySequences`|Bileşik anahtarlarda boş anahtar dizilerinin XSD şema doğrulaması tarafından göz ardı edilip edilemeyeceğini denetler. Daha fazla bilgi için [bkz: Azaltma: XML Şema Doğrulama.](../../../migration-guide/mitigation-xml-schema-validation.md)|.NET Framework 4.6|

> [!NOTE]
> Bir uygulama `AppContextSwitchOverrides` yapılandırma dosyasına öğe eklemek yerine, (C#' da) `static` veya `Shared` (Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemini arayarak anahtarları programlı olarak ayarlayabilirsiniz.

 Kitaplık geliştiricileri, arayanların kitaplıklarının sonraki sürümlerinde tanıtılan değiştirilmiş işlevleri devre dışı bırakmalarına olanak sağlamak için özel anahtarlar da tanımlayabilir. Daha fazla bilgi <xref:System.AppContext> için sınıfa bakın.

## <a name="switches-in-aspnet-apps"></a>ASP.NET uygulamalarında anahtarlar

web.config dosyasının [ \<appSettings>](../appsettings/index.md) bölümüne [ \<bir>ekle](../appsettings/add-element-for-appsettings.md) öğesi ekleyerek uyumluluk ayarlarını kullanacak ASP.NET bir uygulamayı yapılandırabilirsiniz.

Aşağıdaki örnek, `<add>` bir web.config `<appSettings>` dosyasının bölümüne iki ayar eklemek için öğeyi kullanır:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `Switch.System.Globalization.NoAsyncCurrentCulture` `AppContextSwitchOverrides` asynchronous yöntem çağrılarında kültürün iş parçacıkları arasında akmasını engelleyen tek bir uygulama uyumluluk anahtarı tanımlamak için öğeyi kullanır.

```xml
<configuration>
   <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />
   </runtime>
</configuration>
```

 Aşağıdaki örnek, `AppContextSwitchOverrides` iki uygulama uyumluluk anahtarı tanımlamak `Switch.System.Globalization.NoAsyncCurrentCulture` için `Switch.System.IO.BlockLongPaths`öğeyi kullanır ve. Bir yarı kolon iki ad/değer çiftini ayırır.

```xml
<configuration>
    <runtime>
       <AppContextSwitchOverrides
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />
    </runtime>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 4.6 ve sonraki yıllardaki yeni davranışları azletmek](../../../migration-guide/mitigations.md)
- <xref:System.AppContext?displayProperty=nameWithType>
- [\<çalışma zamanı> Öğesi](runtime-element.md)
- [\<yapılandırma> Element](../configuration-element.md)
