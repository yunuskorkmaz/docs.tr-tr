---
title: '&lt;AppContextSwitchOverrides&gt; öğesi'
ms.custom: updateeachrelease
ms.date: 04/19/2018
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d16ce7f2744869c812b9988e91edd153d9cb4fd2
ms.sourcegitcommit: e8dc507cfdaad504fc9d4c83d28d24569dcef91c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "32747531"
---
# <a name="ltappcontextswitchoverridesgt-element"></a>&lt;AppContextSwitchOverrides&gt; öğesi
Tarafından kullanılan bir veya daha fazla anahtarları tanımlar <xref:System.AppContext> yeni işlevselliği için bir geri çevirme mekanizma sağlar sınıfını.  
  
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
|"name = value"|Değeri ile birlikte bir önceden tanımlanmış bir anahtar adı (`true` veya `false`). Birden çok anahtar ad/değer çiftleri noktalı virgül ile ayrılır (";"). .NET Framework tarafından desteklenen önceden tanımlanmış bir anahtar adları listesi için Açıklamalar bölümüne bakın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 4.6 ile başlayan `<AppContextSwitchOverrides>` öğesi bir yapılandırma dosyasına yönelik bir API uygulamasının yeni işlevsellikten yararlanmak veya bir kitaplık önceki sürümleriyle uyumluluğu korumak belirlemek için sağlar. Örneğin, bir API davranışını iki bir kitaplık sürümleri arasında değiştirildi `<AppContextSwitchOverrides>` öğesi çağıranlar dışında yeni işlevselliği desteklemek kitaplık sürümleri üzerinde yeni davranış geri çevirmek için bu API sağlar. .NET Framework'teki API'leri çağıran uygulamalar için `<AppContextSwitchOverrides>` öğe ayrıca uygulamaları uygulamalarını içeren .NET Framework sürümünde çalışıyorsa yeni işlevselliği geri çevirmek için .NET Framework'ün önceki bir sürümü hedeflemek çağıranlar izin ver işlevselliği.  
  
 `value` Özniteliği `<AppContextSwitchOverrides>` öğesi bir veya daha fazla noktalı virgülle ayrılmış ad/değer çiftleri içeren tek bir dizenin oluşur.  Her ad bir uyumluluk anahtarı tanımlar ve karşılık gelen değeri bir Boole değeri (`true` veya `false`) anahtar ayarlanmış olup olmadığını gösterir. Varsayılan olarak, anahtarıdır `false`, ve kitaplıkları yeni işlevsellik sağlar. Anahtar ayarlanmışsa yalnızca önceki işlevsellik sağlarlar (diğer bir deyişle, değerdir `true`). Bu, yeni işlevsellik geri çevirmek için önceki davranışı bağımlı arayanlara izin verirken için mevcut bir API'ye yeni davranış sağlamak kitaplıkları sağlar.  
  
 .NET Framework, aşağıdaki anahtarlar destekler:  
  
|Anahtar adı|Açıklama|Tanıtılan|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Windows Presentation Foundation denetim düzeni için eski bir algoritma kullanıp kullanmadığını denetler. Daha fazla bilgi için [azaltma: WPF düzeni](~/docs/framework/migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Bir paket bölümlerini imzalamak için PackageDigitalSignatureManager tarafından kullanılan varsayılan algoritma SHA1 veya SHA256 olup olmadığını denetler.|.NET framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Ayarlandığında `false`, FIPS etkin olduğunda XAML tabanlı iş akışı projeleri Visual Studio ile hata ayıklamasını sağlar. Bu olmadan, bir <xref:System.NullReferenceException> System.Activities derlemedeki yöntemlere yapılan çağrılar oluşturulur.|.NET framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Hata ayıklayıcı bir iş akışı örneği için sağlama toplamı MD5 veya SHA1 kullanıp kullanmadığını denetler. | .NET framework 4.7|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Denetimleri olup yığın izlemelerini taşınabilir pdb kullanırken elde kaynak dosya ve satır bilgileri içerir. `false` Kaynak dosya ve satır bilgilerini dahil etmek için; Aksi takdirde, `true`.|.NET framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Denetimleri olup olmadığını <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> yöntemi bir özel durum oluşturursa, bir <xref:System.Drawing.Icon> nesnenin PNG çerçeve vardır. Daha fazla bilgi için [azaltma: simge nesneleri PNG çerçevelerde](~/docs/framework/migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|  
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Belirler olmadığını <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> koleksiyonu eklendiğinde, nesneler atıldı düzgün <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> yöntemi. `true` eski davranışı korumak için; `false` tüm özel yazı tipi nesneleri atmak için. |.NET framework 4.7.2|
|`Switch.System.Drawing.Printing.`</br>`OptimizePrintPreview`|Denetimleri olmadığını performansını <xref:System.Windows.Forms.PrintPreviewDialog> ağ yazıcıları için optimize edilmiştir. Daha fazla bilgi için [PrintPreviewDialog denetimine genel bakış](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Zaman uyumsuz işlemler çağıran iş parçacığının bağlamında geçmez olup olmadığını denetler. Daha fazla bilgi için [CurrentCulture ve CurrentUICulture akışı görevleri arasında](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Denetimleri olmadığını <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> yöntemi yalnızca son DNS girişi ile talep türüyle eşleşen dener. Daha fazla bilgi için [azaltma: X509CertificateClaimSet.FindClaims yöntemi](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Değişebilir bir nesne döndürülecek AuthorizationContext.Empty izin verilip verilmeyeceğini denetler.|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|Denetimleri olmadığını daha uzun yollar `MAX_PATH` throw (260 karakter) bir <xref:System.IO.PathTooLongException>. Daha fazla bilgi için [uzun yol Destek](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Yerel işletim sistemi rutinleri tarafından açma için kullanılıp kullanılmadığını denetler <xref:System.IO.Compression.DeflateStream> sınıfı. `false` Yerel API'lerin kullanmak için; `true` kullanılacak <xref:System.IO.Compression.DeflateStream> uygulaması.|.NET framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Ters eğik çizgi kullanır ("\\") yerine eğik çizgi ("/") yol ayırıcı olarak <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> özelliği. Daha fazla bilgi için [azaltma: ZipArchiveEntry.FullName yol ayırıcı](~/docs/framework/migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|İşletim sistem özel durumlarını ile oluşturulmuş bir arka plan iş parçacığı üzerinde oluşturulan denetler <xref:System.IO.Ports.SerialPort> akışları işlemi sonlandırın.|.NET framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Eski yolu normalleştirme kullanılır ve tarafından desteklenen URI yolları denetimleri <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemleri. Daha fazla bilgi için [azaltma: yol normalleştirme](~/docs/framework/migration-guide/mitigation-path-normalization.md) ve [azaltma: iki nokta üst üste yolu denetler](~/docs/framework/migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|  
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Bir test için eşitlik karşılaştırır denetler <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> özelliği ile bir nesnenin <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> özelliği ikinci nesne. Daha fazla bilgi için [MemberDescriptor.Equals yanlış uygulaması](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Devre dışı bırakır, Gelişmiş anahtar kullanımı (EKU) nesnenin tanımlayıcısını (OID) doğrulama sertifikası. Bir anahtarı kullanan uygulamaları gösteren, nesne tanımlayıcıları (OID) koleksiyonunu bir Gelişmiş anahtar kullanımı (EKU) uzantısıdır.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|TLS1.0 tarayıcı yararlanma karşı SSL/TLS (BEAST) azaltma SCH_SEND_AUX_RECORD kullanımını devre dışı bırakılarak devre dışı bırakır.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Denetimleri olmadığını <xref:System.Net.ServicePointManager?displayProperty=nameWithType> ve <xref:System.Net.Security.SslStream?displayProperty=nameWithType> sınıfları, SSL 3.0 protokolünü kullanabilirsiniz. Daha fazla bilgi için [azaltma: TLS protokolleri](~/docs/framework/migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|SystemDefault TLS sürümlerini dönüştürme geri Tls12 Tls11, Tls varsayılan olarak devre dışı bırakır.|.NET framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|SslStream TLS sunucu tarafı uyarıları devre dışı bırakır.|.NET framework 4.7|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Denetimleri olmadığını [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) ECMAScript V6 ve V8 standartlarına göre bazı denetim karakterleri serileştirir. Daha fazla bilgi için [azaltma: DataContractJsonSerializer ile denetim karakterlerini seri hale getirme](Mitigation:%20Serialization%20of%20Control%20Characters%20with%20the%20DataContractJsonSerializer.md)| .NET framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Denetimleri olmadığını <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> birden çok ayarlamaları veya yalnızca tek bir düzeltmesi için bir saat dilimi destekler. Varsa `true`, kullandığı <xref:System.TimeZoneInfo> serileştirmek için türü ve tarih ve saat verileri seri durumdan; Aksi takdirde kullanır <xref:System.TimeZone> birden çok ayarlama kuralları desteklemeyen türü.|.NET Framework 4.6.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Denetimleri olmadığını <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> Oluşturucu, yeni nesnenin ayarlar <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> özelliği ile var olan bir nesne başvurusu. Daha fazla bilgi için [azaltma: Claimsıdentity Oluşturucusu](~/docs/framework/migration-guide/mitigation-claimsidentity-constructor.md).|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Denetimleri olmadığını yeniden denemesi bir <xref:System.Security.Cryptography.AesCryptoServiceProvider> şifre çözücü oluşturur bir <xref:System.Security.Cryptography.CryptographicException>. Daha fazla bilgi için [AesCryptoServiceProvider şifre çözücü yeniden kullanılabilir bir dönüştürme sağlar](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Denetimleri olmadığını değerini [CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) özelliği bir [IntPtr](xref:System.IntPtr) pencere bellek konumunu temsil işlemek veya bir pencere tutucu (HWND) olup. Daha fazla bilgi için [azaltma: CspParameters.ParentWindowHandle bekliyor HWND](Mitigation:%20CspParameters.ParentWindowHandle%20Expects%20an%20HWND.md). |.NET framework 4.7|   
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Bazı SignedCMS işlemleri için varsayılan, SHA1 veya SHA256 olup olmadığını belirler. |.NET framework 4.7.1|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Bazı SignedXML işlemleri için varsayılan, SHA1 veya SHA256 olup olmadığını belirler. |.NET framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Belirler olmadığını `TransportWithMessageCredential` güvenlik modu sağlar imzasız iletilerle "Kime" üst bilgisinde. Katılımı anahtar budur. Daha fazla bilgi için [.NET Framework 4.6.1 çalışma zamanı değişiklikleri](https://msdn.microsoft.com/library/mt592686.aspx#WCF).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Denetimleri olmadığını <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> Oluşturucusu oluşturur bir <xref:System.ArgumentException> öğeler ise `null`.|.NET framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|İle X509 kullanma girişimi sertifikaları olmadığını CSG anahtar depolama sağlayıcısı, bir özel durum oluşturur. belirler. Daha fazla bilgi için [WCF aktarım güvenliği destekleyen CNG kullanarak depolanan sertifikaları](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|HTTP taşıma şirket içinde barındırılan bir hizmetle kullanırken, bu değeri ayarlamak `true` neden olan bir uygulama eklendiğinde yok saymak WCF `Connection: close` üst bilgisi için bir istek için yanıt üstbilgileri. Bu değeri ayarlamak `false` sağlayan ekleme `Connection: close` yanıt üstbilgileri için bir yanıt gönderildikten sonra isteği yuva kapatma sonuçları başlığı.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Tek bir iş parçacığına aynı anda yürütme desteklemeyeceğini bir hizmetin örneklerine kısıtlama neden kilitlenmeleri işler.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|İle birlikte `Switch.System.Net.DontEnableSchUseStrongCrypto`, WCF ileti güvenliği TLS 1.1 ve TLS 1.2 kullanıp kullanmadığını belirler.|.NET framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|Değerini `false` işletim sisteminin protokol için varsayılan yapılandırmayı ayarlar. Değerini `true` kullanılabilen en yüksek protokol için varsayılan ayarlar. (Ayrıca bakım dalı önceki framework sürümlerinin üzerinde kullanılabilir)|.NET framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|İmza algoritması wcf'de MSMQ iletileri için varsayılan ileti SHA1 veya SHA256 olup olmadığını belirler.|.NET framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|WCF için adlandırılmış kanallar rastgele adı oluşturmada kullanılacak bir SHA1 veya SHA256 karma kullanıp kullanmadığını denetler.|.NET framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Throw verilip verilmeyeceğini denetler bir [NullReferenceException](xref:System.NullReferenceException) özel durum iletisi olduğunda null.|.NET framework 4.7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Hizmet başlangıç sırasında oluşturulan özel durumlar çağıran yayılır denetimleri <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> yöntemi.|.NET framework 4.7.1|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Bazen kodu belirli yüzde olarak kodlanmış karakterler artık tutarlı bir şekilde sol kodlanmış olup olmadığını belirler. Varsa `true`, bunlar kodu çözülmüş; Aksi takdirde `false`.|.NET framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Unicode çift yönlü karakter URI'ler işlenmesini belirler. `true` bir URI'leri Şerit bunları çoğaltmak; `false` koruyabilir ve bunları yüzde olarak kodlamak için.|.NET framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Windows Presentation Foundation eski bir algoritma geçerli olup olmadığını belirler (`true`) veya yeni bir algoritma (`false`) için alan ayırma, \*-sütun. Daha fazla bilgi için [azaltma: kılavuz denetim alanı ayırma yıldız sütunlara](Mitigation:%20Grid%20Control's%20Space%20Allocation%20to%20Star-columns.md). |.NET framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Değişti olayı denetimleri olup bir seçici veya bir sekme denetimini her zaman seçimi tetiklenmeden önce seçili değer özelliğinin değerini güncelleştirir.|.NET framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Donatıcı olmayan temel seçimi işleme için kullanılabilir olup olmadığını belirler <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.PasswordBox> occluded metin önlemek için denetimleri (`false`), veya metin yalnızca donatıcı katmanındaki olup işlenir (`true`).|.NET framework 4.7.2|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|DPI bir sistem üzerinde değişiklikler olup olmadığını belirler (değerini `false`) veya İzleyici başına temelinde (değerini `true`).|.NET Framework 4.6.2|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Geliştirici özel olarak işlemek gereken olup olmadığını belirleyen <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> denetim metin mevcut olduğunda eylem. `true` İşlenecek <xref:System.Windows.Forms.DomainUpDown.UpButton> eylem; `false` için <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> ve <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> düzgün bir şekilde eşitlenmiş olması için Eylemler.|.NET framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Özel bir izin veren kodların dışına bölgedeyse <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> bir özel durum oluşturmadan iletileri güvenli bir şekilde filtrelemek için uygulama olduğunda <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> yöntemi çağrılır. Daha fazla bilgi için [azaltma: özel IMessageFilter.PreFilterMessage uygulamaları](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|  
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Belirler olmadığını <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> özelliği kullanıcı menü bir iç içe geçmiş açıldığında kaynak denetimi döndürür <xref:System.Windows.Forms.ToolStripMenuItem> denetimi. `true` Döndürülecek `null`, eski davranışı; `false` kaynak denetimi dönün.|.NET framework 4.7.2|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|İsteğe bağlı olup olmadığını belirleyen `WM_POINTER`-temel dokunma/ekran kalemi yığın WPF uygulamalarında etkinleştirilir. Daha fazla bilgi için [azaltma: işaretçi tabanlı dokunmatik ve Kalem desteği](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|SHA256 sağlama toplamları için kullanılan varsayılan karma algoritması olup olmadığını belirler (`false`) veya SHA1 (`true`).|.NET framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Eski olmadığını denetler [NullReferenceException](xref:System.NullReferenceException) daha açık belirtmek gerekirse özel durumun nedenini belirten yerine özel durum (gibi bir [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) veya bir [ Derleme işlemi FileNotFoundException](xref:System.IO.FileNotFoundException). Üzerinde işleme bağlı olan kod tarafından kullanılması amaçlanmıştır [NullReferenceException](xref:System.NullReferenceException). | .NET framework 4.7 |
|`Switch.UseLegacyAccessibilityFeatures`|Kullanılabilir .NET Framework 4.7.1 ile başlayarak erişilebilirlik özelliği olup olmadığını kontrol eder etkin veya devre dışı. | .NET framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Denetimlerin erişilebilirlik 4.7.2 .NET Framework'de kullanılabilen özelliği etkinleştirilir (`false`) veya devre dışı (`true`). Varsa `true`, `Switch.UseLegacyAccessibilityFeatures` ayrıca olmalıdır `true` .NET Framework 4.7.1 erişilebilirlik özelliklerini etkinleştirmek için.|.NET framework 4.7.2|
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Bileşik anahtarlar boş anahtar sıralarında XSD şema doğrulaması tarafından göz ardı edilir olup olmadığını denetler. Daha fazla bilgi için [azaltma: XML şema doğrulaması](~/docs/framework/migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|  
  
> [!NOTE]
>  Eklemek yerine bir `AppContextSwitchOverrides` öğesi uygulama yapılandırma dosyası için de ayarlayabilirsiniz anahtarlar program aracılığıyla çağırarak `static` (C# ' de) veya `Shared` (Visual Basic'te) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemi.  
  
 Kitaplık geliştiricilerin kitaplıklarının sonraki sürümlerde değiştirilmiş işlev dışında bırakmak arayanlara izin vermek için özel anahtarlar da tanımlayabilirsiniz. Daha fazla bilgi için <xref:System.AppContext> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `AppContextSwitchOverrides` tek bir uygulama uyumluluk anahtarı tanımlamak için `Switch.System.Globalization.NoAsyncCurrentCulture`, engelleyen kültür zaman uyumsuz yöntem çağrısı iş parçacıkları arasında akar.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 Aşağıdaki örnekte `AppContextSwitchOverrides` iki uygulama uyumluluk anahtarları tanımlamak için `Switch.System.Globalization.NoAsyncCurrentCulture` ve `Switch.System.IO.BlockLongPaths`. Noktalı virgül iki ad/değer çiftlerini ayırır unutmayın.  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.AppContext?displayProperty=nameWithType>  
 [\<çalışma zamanı > öğesi](runtime-element.md)  
 [\<Yapılandırma > öğesi](../configuration-element.md)
