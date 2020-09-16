---
title: AppContextSwitchOverrides öğesi
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
ms.openlocfilehash: 0ead35559a17eb06304e6c251d2fe388ca178a30
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552290"
---
# <a name="appcontextswitchoverrides-element"></a>\<AppContextSwitchOverrides> öğesi

<xref:System.AppContext>Yeni işlevlere yönelik bir geri alma mekanizması sağlamak için sınıfı tarafından kullanılan bir veya daha fazla anahtarı tanımlar.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<AppContextSwitchOverrides>**

## <a name="syntax"></a>Syntax

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

|Değer|Açıklama|
|-----------|-----------------|
|"ad = değer"|Önceden tanımlanmış bir anahtar adı ( `true` veya) değeriyle birlikte `false` . Birden çok anahtar adı/değer çifti noktalı virgülle (";") ayrılır. .NET Framework tarafından desteklenen önceden tanımlanmış anahtar adlarının bir listesi için, açıklamalar bölümüne bakın.|

### <a name="child-elements"></a>Alt Öğeler
 Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar
 .NET Framework 4,6 ' den başlayarak, `<AppContextSwitchOverrides>` bir yapılandırma dosyasındaki öğesi, BIR API 'nin çağıranlarının, uygulamanın yeni işlevlerden faydalanıp yararlanamayacağını veya bir kitaplığın önceki sürümleriyle uyumluluğunu koruyabilmesine izin verir. Örneğin, bir API 'nin davranışı iki bir kitaplığın sürümü arasında değiştiyse, `<AppContextSwitchOverrides>` öğesi bu API 'nin çağıranlarının yeni işlevselliği destekleyen kitaplık sürümlerindeki yeni davranışı geri almasına izin verir. .NET Framework API 'Leri çağıran uygulamalar için, `<AppContextSwitchOverrides>` Bu işlevi içeren bir .NET Framework sürümünde çalışıyorsa, uygulamaları, uygulamalar .NET Framework daha önceki bir sürümünü hedefleyen çağıranlar için yeni işlevselliği kabul edebilir.

 `value` `<AppContextSwitchOverrides>` Öğesinin özniteliği bir veya daha fazla noktalı virgülle ayrılmış ad/değer çiftlerinden oluşan tek bir dizeden oluşur.  Her ad bir uyumluluk anahtarını tanımlar ve buna karşılık gelen değer, `true` `false` anahtarın ayarlanmış olup olmadığını belirten bir Boolean (veya) değeridir. Varsayılan olarak, anahtarı, `false` ve kitaplıkları yeni işlevleri sağlar. Yalnızca, anahtar ayarlanmışsa (yani, değeri ise) önceki işlevselliği sağlarlar `true` . Bu, kitaplıkların var olan bir API için yeni davranış sağlamasına izin verirken önceki davranışa bağlı olan çağıranların yeni işlevselliği devre dışı vermesini sağlar.

.NET Framework aşağıdaki anahtarları destekler:

|Anahtar adı|Description|Dağıtıla|
|-----------------|-----------------|----------------|
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Windows Presentation Foundation denetim düzeni için eski bir algoritmayı kullanıp kullanmadığını denetler. Daha fazla bilgi için bkz. [azaltma: WPF düzeni](../../../migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|PackageDigitalSignatureManager tarafından bir paketin parçalarını imzalamak için kullanılan varsayılan algoritmanın SHA1 veya SHA256 olup olmadığını denetler.<br>SHA1 ile ilgili çakışma sorunları nedeniyle Microsoft SHA256 önerir.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Olarak ayarlandığında `false` , FIPS etkin olduğunda Visual Studio Ile XAML tabanlı iş akışı projelerinin hata ayıklamasına izin verir. Bu olmadan, <xref:System.NullReferenceException> System. Activities derlemesinde yöntemlere çağrılar halinde bir oluşturulur.| .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Hata ayıklayıcı içindeki bir iş akışı örneği için sağlama toplamı, MD5 veya SHA1 kullanıp kullanmadığını denetler. |  .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|İş akışı sağlama toplamı karmasının, .NET Framework 4,7 () içinde varsayılan olarak tanıtılan SHA1 algoritmasını `true` veya .NET Framework 4,8 () içinde varsayılan olarak tanıtılan varsayılan sha256 algoritmasını kullanıp kullanmadığını denetler `false` .<br>SHA1 ile ilgili çakışma sorunları nedeniyle Microsoft SHA256 önerir.| .NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Taşınabilir pdb 'leri kullanırken yığın izlemelerinin elde edilip edilmeyeceğini denetler ve kaynak dosya ve satır bilgileri içerebilir. `false` Kaynak dosya ve satır bilgilerini dahil etmek için; Aksi takdirde, `true` .| .NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType>Bir <xref:System.Drawing.Icon> nesne png çerçevelerindeyken yöntemin bir özel durum oluşturulup oluşturulmayacağını denetler. Daha fazla bilgi için bkz. [azaltma: simge NESNELERINDE png çerçeveleri](../../../migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|<xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType>Yöntem tarafından koleksiyona eklendiğinde nesnelerin düzgün şekilde atılıp atılmayacağını belirler <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> . `true` eski davranışı korumak için; `false` tüm özel yazı tipi nesnelerini atmak için. | .NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Performansının, <xref:System.Windows.Forms.PrintPreviewDialog> ağ yazıcıları için en iyi duruma getirilip getirilmediğini denetler. Daha fazla bilgi için bkz. [Printönizleme Iletişim kutusu denetimine genel bakış](/dotnet/desktop/winforms/controls/printpreviewdialog-control-overview-windows-forms).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Yıl aralığının Japonca takvim için olup olmadığını denetler. `true` yıl aralığı denetimlerini zorlamak ve `false` devre dışı bırakmak için (varsayılan davranış). Daha fazla bilgi için bkz. [takvimler Ile çalışma](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Yalnızca "1" öğesinin ayrıştırma işlemlerinde bir Japonca takvim dönemi için ilk yıl olarak tanınıp tanınmadığını denetler. `true` yalnızca "1" öğesini tanımak için `false` "1" veya gannen (varsayılan davranış) öğesini tanımak için. Daha fazla bilgi için bkz. [takvimler Ile çalışma](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Japonca takvim çağının ilk yılının, biçimlendirme işlemlerinde "1" veya gannen olarak temsil edilip edilmeyeceğini denetler. `true` çağın ilk yılını "1" olarak biçimlendirmek için `false` bunu gannen olarak biçimlendirmek için (varsayılan davranış). Daha fazla bilgi için bkz. [takvimler Ile çalışma](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Zaman uyumsuz işlemlerin çağıran iş parçacığının bağlamından akış yapıp yapamadığını denetler. Daha fazla bilgi için bkz. [Görevler arasında CurrentCulture ve CurrentUICulture Flow](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType>Yöntemin yalnızca son DNS girdisiyle talep türü ile eşleştirmeye çalışıp çalışmadığını denetler. Daha fazla bilgi için bkz. [azaltma: X509CertificateClaimSet. Findclaim metodu](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|AuthorizationContext. Empty 'in kesilebilir bir nesne döndürmesini izin verip vermeyeceğinizi denetler.|.NET Framework 4.6|
|`Switch.System.IO.BlockLongPaths`|(260 karakter) karakterden daha uzun bir yol olup olmadığını denetler `MAX_PATH` <xref:System.IO.PathTooLongException> . Daha fazla bilgi için bkz. [uzun yol desteği](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Sınıf tarafından açma için yerel işletim sistemi yordamlarının kullanılıp kullanılmadığını denetler <xref:System.IO.Compression.DeflateStream> . `false` Yerel API 'Leri kullanmak için; `true` <xref:System.IO.Compression.DeflateStream> uygulamasını kullanın.| .NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|\\Özelliğindeki yol ayırıcısı olarak eğik çizgi ("/") yerine ters eğik çizgi ("") kullanır <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> . Daha fazla bilgi için bkz.  [azaltma: ZipArchiveEntry. FullName yol ayırıcısı](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Akışlarla oluşturulan arka plan iş parçacıklarında oluşan işletim sistemi özel durumlarının <xref:System.IO.Ports.SerialPort> işlemi sonlandırır.|.NET Framework 4.7.1|
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Eski yol normalleştirme kullanılıp kullanılmadığını ve URI yollarının ve yöntemleri tarafından desteklenip desteklenmediğini denetler <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> . Daha fazla bilgi için bkz. [azaltma: yol normalleştirme](../../../migration-guide/mitigation-path-normalization.md) ve [azaltma: yol iki nokta denetimleri](../../../migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Bir eşitlik testinin, <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> bir nesnenin özelliğini ikinci nesnenin özelliğiyle karşılaştırıp karşılaştırmadığını denetler <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> . Daha fazla bilgi için bkz. [MemberDescriptor. Equals Için hatalı uygulama](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Sertifika Gelişmiş anahtar kullanımı (EKU) nesne tanımlayıcısı (OID) doğrulamasını devre dışı bırakır. Gelişmiş anahtar kullanımı (EKU) uzantısı, anahtarı kullanan uygulamaları belirten bir nesne tanımlayıcıları (OID) koleksiyonudur.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|SCH_SEND_AUX_RECORD kullanımını devre dışı bırakarak SSL/TLS (BEAST) azaltma için TLS 1.0 tarayıcı açığından yararlanmaya devre dışı bırakır.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|<xref:System.Net.ServicePointManager?displayProperty=nameWithType>Ve <xref:System.Net.Security.SslStream?displayProperty=nameWithType> sınıflarının SSL 3,0 protokolünü kullanıp kullanamayacağını denetler. Daha fazla bilgi için bkz. [azaltma: TLS protokolleri](../../../migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Varsayılan bir Tls12, Tls11, TLS geri dönerek SystemDefault TLS sürümlerini devre dışı bırakır.| .NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|SslStream TLS sunucu tarafı uyarılarını devre dışı bırakır.| .NET Framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|COM birlikte çalışma olaylardaki ByRef SafeArray parametrelerinin yerel koda () geri doğru bir şekilde hazırlanıp () `false` veya yerel koda geri hazırlama devre dışı olup olmadığını denetler ( `true` ).| .NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |[DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) 'ın, ECMAScript V6 ve V8 standartlarına göre bazı denetim karakterlerini seri hale getirip getirmediğini denetler. Daha fazla bilgi için bkz [. azaltma: denetim karakterlerinin DataContractJsonSerializer Ile serileştirilmesi](../../../migration-guide/mitigation-serialization-control-characters.md)|  .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|' Nin <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> birden çok ayarlamayı veya bir saat dilimi için yalnızca tek ayarlamayı destekleyip desteklemediğini denetler. `true`Bu, <xref:System.TimeZoneInfo> Tarih ve saat verilerini seri hale getirmek ve seri durumdan çıkarmak için türünü kullanır; Aksi takdirde, <xref:System.TimeZone> birden çok ayarlama kuralını desteklemeyen türünü kullanır.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|<xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType>Nesne serileştirme ve seri durumundan çıkarma sırasında daha büyük bir dizi boyutu kullanıp kullanmadığını denetler. `true`Büyük nesne grafiklerinin serileştirme ve serisini kaldırma performansını geliştirmek için, gibi türlerine göre bu anahtarı olarak ayarlayın <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> . | .NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|<xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29>Oluşturucunun yeni nesnenin <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> özelliğini varolan bir nesne başvurusuyla ayarlamayacağını denetler. Daha fazla bilgi için bkz. [azaltma: ClaimsIdentity Oluşturucusu](../../../migration-guide/retargeting/4.6.1-4.6.2.md).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Bir şifre çözücü yeniden kullanma denemesinin bir oluşturuyor olup olmadığını denetler <xref:System.Security.Cryptography.AesCryptoServiceProvider> <xref:System.Security.Cryptography.CryptographicException> . Daha fazla bilgi için bkz. [AesCryptoServiceProvider şifre çözücü yeniden kullanılabilir bir dönüşüm sağlar](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|[CspParameters. ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) özelliğinin değerinin bir pencere tanıtıcısının bellek konumunu temsil eden bir [IntPtr](xref:System.IntPtr) veya bir pencere tutamacı (bir hwnd) olup olmadığını denetler. Daha fazla bilgi için bkz [. azaltma: CspParameters. ParentWindowHandle BIR HWND bekliyor](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value). | .NET Framework 4.7|
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|FIPS modunda yönetilen şifreleme sınıflarının kullanılması bir <xref:System.Security.Cryptography.CryptographicException> ( `true` ) mi yoksa sistem kitaplıklarının () uygulamasına mı bağımlı olduğunu denetler `false` .| .NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Bazı SignedCMS işlemleri için varsayılanın SHA1 veya SHA256 olup olmadığını belirler.<br>SHA1 ile ilgili çakışma sorunları nedeniyle Microsoft SHA256 önerir.|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|<xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType>Metodun, işletim sistemi tarafından desteklenen tüm adlandırılmış eğrileri doğru bir şekilde işlediğini `false` veya eski davranışa geri dönmediğini denetler.| .NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Bazı SignedXML işlemleri için varsayılanın SHA1 mi yoksa SHA256 mi olduğunu belirler.<br>SHA1 ile ilgili çakışma sorunları nedeniyle Microsoft SHA256 önerir.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|`TransportWithMessageCredential`Güvenlik modunun imzasız "to" üst bilgisine sahip iletilere izin verip içermediğini belirler. Bu bir kabul etme anahtarıdır. Daha fazla bilgi için bkz. [4.6.1 .NET Framework çalışma zamanı değişiklikleri](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>Oluşturucunun öğelerinden biri olup olmadığını denetler <xref:System.ArgumentException> `null` .|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Bir CSG anahtar depolama sağlayıcısıyla x509 sertifikalarını kullanma denemesinin bir özel durum oluşturursa belirler. Daha fazla bilgi için bkz. [WCF Aktarım GÜVENLIĞI CNG kullanılarak depolanan sertifikaları destekler](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|Şirket içinde barındırılan bir hizmetle HTTP taşıması kullanılırken, bu değeri ayarlamak `true` WCF 'nin `Connection: close` bir isteğin yanıt üst bilgilerine üst bilgi ekleyen bir uygulamayı yok saymasına neden olur. Bu değerin, yanıt `false` üst bilgilerine eklenmesini sağlamak için `Connection: close` , bir yanıt gönderildikten sonra istek yuvasını kapatmaya neden olacak şekilde ayarlanması sağlanır.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Bir re-entrant hizmetinin örneklerinin bir seferde tek bir yürütme iş parçacığı ile kısıtlanması sonucunda oluşan kilitlenmeleri işler.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|İle birlikte `Switch.System.Net.DontEnableSchUseStrongCrypto` , WCF ileti GÜVENLIĞININ tls 1,1 ve tls 1,2 kullanıp kullanmadığını belirler.| .NET Framework 4.7 |
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|Bir değeri `false` , işletim sisteminin Protokolü seçmesini sağlamak için varsayılan yapılandırmayı ayarlar. Bir değeri `true` Varsayılan olarak kullanılabilir en yüksek protokol olarak ayarlar. (Önceki Framework sürümlerinin hizmet dalında de kullanılabilir)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|WCF 'de MSMQ iletileri için varsayılan ileti imzalama algoritmasının SHA1 mi yoksa SHA256 mi olduğunu belirler.<br>SHA1 ile ilgili çakışma sorunları nedeniyle Microsoft SHA256 önerir.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|WCF 'nin adlandırılmış kanallar için rastgele adlar oluşturmak üzere bir SHA1 veya SHA256 karması kullanıp kullanmadığını denetler.<br>SHA1 ile ilgili çakışma sorunları nedeniyle Microsoft SHA256 önerir.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Özel durum iletisi null olduğunda bir [NullReferenceException](xref:System.NullReferenceException) mi oluşturulup oluşturulmayacağını denetler.| .NET Framework 4.7|
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Hizmet başlangıcında oluşturulan özel durumların yöntemi çağırana yayıp yayılmayacağını denetler <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> .|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|<xref:System.Threading.Timer>Örneklerin yüksek ölçekli ortamlar için performans geliştirmelerinden faydalanıp yararlanmadığını denetler. `true`Performans iyileştirmeleri etkinse; `false` (varsayılan değer), devre dışı bırakılır.| .NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Bazen çözülmüş olan belirli yüzde kodlamalı karakterlerin artık tutarlı bir şekilde kodlanmış olduğunu belirler. Varsa, `true` bunlar kodu çözülür; Aksi takdirde, `false` .| .NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|URI 'Lerinde Unicode çift yönlü karakterlerin işlenmesini belirler. `true` Bunları URI 'lerden atmak için `false` bunları korumak ve yüzde kodlamak için.| .NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Windows Presentation Foundation `true` `false` , sütunların sütun ayrılırken eski bir algoritma () veya yeni bir algoritma () uygulanıp uygulanmadığını belirler \* . Daha fazla bilgi için bkz. [azaltma: Grid denetiminin boşluk tahsisi Için yıldız-sütun](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns). | .NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Seçim değiştirilen olayı oluşturmadan önce bir seçicinin veya sekme denetiminin her zaman seçili değer özelliğinin değerini güncelleştirip güncelleştirmediğini denetler.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|' In ve denetim için donatıcı tabanlı seçme oluşturma için kullanılabilir olup olmadığını <xref:System.Windows.Controls.TextBox> belirler <xref:System.Windows.Controls.PasswordBox> ( `false` ) veya metnin yalnızca donatıcı katmanında () işlenip işlenmeyeceği `true` .| .NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Özel IList dizin oluşturucularının `true` , sınıf tarafından yanlış bir şekilde () veya doğru () kullanılıp kullanılmadığını denetler `false` <xref:System.Windows.Data.Binding?displayProperty=nameWithType> .| .NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|DPı değişikliklerinin sistem başına mı (bir değer `false` ) yoksa tek tek izleyici temelinde mi (bir değeri) olacağını belirler `true` .|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|WPF 'nin izleyici tanıma modunda çalıştırıldığı sırada bir içindeki denetimlerin boyutlandırılmasına yönelik iyileştirmelerin <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> devre dışı bırakılıp bırakılmadığını denetler ( `true` ) veya etkin ( `false` ).| .NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Denetim metni mevcut olduğunda geliştiricinin eylemi özel olarak işlemesi gerekip gerekmediğini belirler <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> . `true` eylemi işlemek için <xref:System.Windows.Forms.DomainUpDown.UpButton> ; `false` <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> eylemlerinin doğru şekilde eşitlenmesi için.| .NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Özel bir <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulamanın, yöntemi çağrıldığında bir özel durum oluşturmadan iletileri güvenli bir şekilde filtrelemesine olanak tanıyan kodun dışına çıkma <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> . Daha fazla bilgi için bkz. [azaltma: Custom IMessageFilter. PreFilterMessage uygulamaları](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>Kullanıcı menüyü iç içe geçmiş bir denetimden açtığında özelliğin kaynak denetimini döndürüp döndürmeyeceğini belirler <xref:System.Windows.Forms.ToolStripMenuItem> . `true``null` `false` kaynak denetimi döndürmek için eski davranışı;.| .NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Araç ipucu çağırma desteğinin devre dışı ( `true` ) veya etkin () olup olmadığını denetler `false` . Araç ipucu çağırma desteğinin etkinleştirilmesi, tarafından tanımlanan eski erişilebilirlik özelliklerinin yanı sıra `Switch.UseLegacyAccessibilityFeatures` `Switch.UseLegacyAccessibilityFeatures.2` `Switch.UseLegacyAccessibilityFeatures.3` devre dışı bırakılması (olarak ayarlanır `false` ) gerekir.| .NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|WPF uygulamalarında isteğe bağlı `WM_POINTER` tabanlı bir dokunmatik/Stilus yığınının etkinleştirilip etkinleştirilmediğini belirler. Daha fazla bilgi için bkz [. azaltma: işaretçi tabanlı dokunmatik ve ekran kalemi desteği](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)| .NET Framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Sağlama toplamı için kullanılan varsayılan karma algoritmanın SHA256 ( `false` ) veya SHA1 () olup olmadığını belirler `true` .<br>SHA1 ile ilgili çakışma sorunları nedeniyle Microsoft SHA256 önerir.| .NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Özel durumun nedenini (bir [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) veya bir [FileNotFoundException](xref:System.IO.FileNotFoundException)gibi) daha özel olarak belirten özel durum yerine eski bir [NullReferenceException](xref:System.NullReferenceException) olup olmadığını denetler. [NullReferenceException](xref:System.NullReferenceException)öğesinin işlenmesine bağlı olan kod tarafından kullanılmak üzere tasarlanmıştır. |  .NET Framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|İş akışı proje Derlemeleriyle XOML dosyalarının sağlama toplamı karmasının, MD5 algoritmasını () kullanıp kullanmadığını `true` veya .NET Framework 4,8 ' de varsayılan olarak TANıTıLAN sha256 algoritmasını kullanıp kullanmadığını denetler.<br>MD5 ile ilgili çarpışma sorunları nedeniyle Microsoft SHA256 önerir.| .NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|SqlTrackingService tarafından sağlanan sağlama toplamı karmasının, `true` önbelleğe alınmış dizeler IÇIN MD5 algoritmasını () kullanıp kullanmadığını veya .NET Framework 4,8 ' de varsayılan olarak TANıTıLAN sha256 algoritmasını kullanıp kullanmadığını denetler.<br>MD5 ile ilgili çarpışma sorunları nedeniyle Microsoft SHA256 önerir.| .NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Iş akışı çalışma zamanı tarafından sağlanan sağlama toplamı karmasının, `true` önbelleğe alınmış iş akışı tanımları IÇIN MD5 algoritmasını () kullanıp kullanmadığını veya .NET Framework 4,8 ' de varsayılan olarak TANıTıLAN sha256 algoritmasını kullanıp kullanmadığını denetler.<br>MD5 ile ilgili çarpışma sorunları nedeniyle Microsoft SHA256 önerir.| .NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|.NET Framework 4.7.1 ile başlayan erişilebilirlik özelliklerinin etkin veya devre dışı olup olmadığını denetler. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|.NET Framework 4.7.2 ' de kullanılabilir erişilebilirlik özelliklerinin etkinleştirilip etkinleştirilmediğini denetler () `false` veya devre dışı ( `true` ). `true`Ayrıca, `Switch.UseLegacyAccessibilityFeatures` `true` .NET Framework 4.7.1 erişilebilirlik özelliklerini etkinleştirmek için de olmalıdır.| .NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|.NET Framework 4,8 ' de sunulan erişilebilirlik özelliklerinin etkinleştirilip etkinleştirilmeyeceğini denetler () `false` veya devre dışı ( `true` ). `true`, `Switch.UseLegacyAccessibilityFeatures` Ve de olmalıdır `Switch.UseLegacyAccessibilityFeatures.2` `true` .| .NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|Bir Kullanıcı fare imlecini bir WPF denetimi () üzerine geldiğinde araç ipuçlarının görüntülenip görüntülenmeyeceğini `true` veya hem klavye odağında hem de klavye kısayol tuşu aracılığıyla ( `false` varsayılan davranış) görüntülenip görüntülenmediğini denetler. .NET Framework 4,8 üzerinde çalışan ancak .NET Framework önceki sürümlerini hedefleyen uygulamalar için hem klavye odağını hem de kısayol tuşu desteğini etkinleştirmek için, `Switch.UseLegacyAccessibilityFeatures` `Switch.UseLegacyAccessibilityFeatures.2` ve `Switch.UseLegacyAccessibilityFeatures.3` tümünün olarak ayarlanması gerekir `false` .| .NET Framework 4.8|
|`Switch.System.Xml.`<br />`IgnoreEmptyKeySequences`|Bileşik anahtarlarda boş anahtar sıralarının XSD şema doğrulaması tarafından yoksayılıp yoksayılmadığını denetler. Daha fazla bilgi için bkz. [azaltma: XML şema doğrulaması](../../../migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|

> [!NOTE]
> `AppContextSwitchOverrides`Bir uygulama yapılandırma dosyasına bir öğe eklemek yerine, `static` (C# ' de) veya `Shared` (Visual Basic) yönteminde yöntemini çağırarak anahtarları program aracılığıyla da ayarlayabilirsiniz <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> .

 Kitaplık geliştiricileri, arayanların, kitaplıklarının sonraki sürümlerinde tanıtılan değiştirilmiş işlevselliği devre dışı yapmasına izin vermek için özel anahtarlar da tanımlayabilir. Daha fazla bilgi için, <xref:System.AppContext> sınıfına bakın.

## <a name="switches-in-aspnet-apps"></a>ASP.NET Apps 'teki anahtarlar

[\<Add>](../appsettings/add-element-for-appsettings.md)web.config dosyanın bölümüne bir öğe ekleyerek uyumluluk ayarlarını kullanmak için bir ASP.NET uygulamasını yapılandırabilirsiniz [\<appSettings>](../appsettings/index.md) .

Aşağıdaki örnek, `<add>` `<appSettings>` web.config bir dosyanın bölümüne iki ayar eklemek için öğesini kullanır:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `AppContextSwitchOverrides` tek bir uygulama uyumluluk anahtarı tanımlamak için öğesini kullanır, `Switch.System.Globalization.NoAsyncCurrentCulture` Bu da kültürün zaman uyumsuz yöntem çağrılarında iş parçacıkları arasında akmasını önler.

```xml
<configuration>
   <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />
   </runtime>
</configuration>
```

 Aşağıdaki örnek, `AppContextSwitchOverrides` iki uygulama uyumluluk anahtarı tanımlamak için öğesini kullanır `Switch.System.Globalization.NoAsyncCurrentCulture` `Switch.System.IO.BlockLongPaths` . Noktalı virgül iki ad/değer çiftini ayırır.

```xml
<configuration>
    <runtime>
       <AppContextSwitchOverrides
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />
    </runtime>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 4,6 ve sonraki sürümlerde yeni davranışları azaltma](../../../migration-guide/mitigations.md)
- <xref:System.AppContext?displayProperty=nameWithType>
- [\<runtime> Dosyalarında](runtime-element.md)
- [\<configuration> Dosyalarında](../configuration-element.md)
