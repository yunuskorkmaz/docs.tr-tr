---
title: Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- type libraries [.NET Framework], importing
- importing type library
- Tlbimp.exe
- type definition conversion
- Type Library Importer
- type libraries
- converting type definitions
ms.assetid: ec0a8d63-11b3-4acd-b398-da1e37e97382
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9591c9ced836a98c5843f5fb53809903f72c73f3
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="tlbimpexe-type-library-importer"></a>Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)
Tür Kitaplığı İçeri Aktarma programı, COM tür kitaplığı içinde bulunan tür tanımlarını bir ortak dil çalışma zamanı derlemesi içindeki eşdeğer tanımlara dönüştürür. Tlbimp.exe'nin çıktısı, özgün tür kitaplığı içinde tanımlanan türler için çalışma zamanı meta verileri içeren bir ikili dosyadır (derleme). Bu dosya araçları ile aşağıdaki gibi inceleyebilirsiniz [Ildasm.exe](ildasm-exe-il-disassembler.md).  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
tlbimp tlbFile [options]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*tlbFile*|COM tür kitaplığı içeren herhangi bir dosyanın adı.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/asmversion:** *adı*|Üretilecek derlemenin sürüm numarasını belirtir. Belirtin *versionnumber* biçimde *major.minor.build.revision*.|  
|**/ Company:** `companyinformation`|Şirket bilgilerini çıktı derlemesine ekler.|  
|**Company Copyright:** `copyrightinformation`|Çıktı derlemesine telif hakkı bilgileri ekler. Bu bilgileri görüntülenebilir **dosya özelliklerini** derleme için iletişim kutusu.|  
|**/delaysign**|Elde edilen ve tanımlayıcı bir ada sahip olan derlemeyi gecikmeli imzalama yöntemiyle imzalamak için kullanılacak Tlbimp.exe'yi belirtir. Bu seçenek ile ya da belirtmelisiniz **/keycontainer:**, **/keyfile:**, veya **/publickey:** seçeneği. Gecikmeli imzalama işlemi hakkında daha fazla bilgi için bkz: [Gecikmeli bir derleme imzalama](../app-domains/delay-sign-assembly.md).|  
|**/ Help**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/ keycontainer:** *kapsayıcı adı*|Belirtilen anahtar kapsayıcısı bulunan ortak/özel anahtar çifti kullanarak tanımlayıcı bir ad ile elde edilen derlemeyi imzalar *containername*.|  
|**/ keyfile:** *dosya adı*|Bulunan publisher'ın resmi ortak/özel anahtar çifti kullanarak tanımlayıcı bir ad ile elde edilen derlemeyi imzalar *filename*.|  
|**/Machine:** `machinetype`|Belirtilen makine türünü (mikro işlemci) hedefleyen bir derleme oluşturur. Desteklenen makine türleri: x86, x64, Itanium ve Belirsiz.|  
|**/ Namespace:** *ad alanı*|Derlemenin oluşturulacağı ad alanını belirtir.|  
|**/noclassmembers**|Tlbimp.exe'nin sınıflara üye eklemesini önler. Bu olası önler <xref:System.TypeLoadException>.|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/ out:** *dosya adı*|İçine meta veri tanımlarının yazılacağı çıktı dosyasının, derlemenin ve ad alanının adını belirtir. **/Out** seçeneği varsa derlemenin ad alanı üzerinde hiçbir etkisi tür kitaplığını derleme ad alanını açıkça denetler arabirimi tanım dili (IDL) özel özniteliği belirtir. Bu seçeneği belirtmezseniz, Tlbimp.exe, girdi dosyasında tanımlanan asıl tür kitaplığıyla aynı ada sahip bir dosyaya meta verileri yazar ve ona bir .dll uzantısı atar. Çıktı dosyasının adı girdi dosyasının adıyla aynı ise, araç tür kitaplığı üzerine yazılmasını engellemek için bir hata üretir.|  
|**/ birincil**|Belirtilen tür kitaplığı için bir birincil birlikte çalışma derlemesi oluşturur. Derlemeyi tür kitaplığı yayıncısının oluşturduğunu belirten bilgiler derlemeye eklenir. Birincil birlikte çalışma derlemesi belirterek, bir yayıncının derlemesini, Tlbimp.exe kullanarak tür kitaplığından oluşturulan diğer derlemelerden ayırt edersiniz. Yalnızca kullanmalısınız **/birincil** Tlbimp.exe ile aldığınız tür kitaplığı yayımcısı olup olmadığını seçeneği. Birincil birlikte çalışma derlemesi ile oturum açmanız gerekir Not bir [güçlü ad](../app-domains/strong-named-assemblies.md). Daha fazla bilgi için bkz: [birincil birlikte çalışma derlemeleri](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).|  
|**/Product:** `productinformation`|Çıktı derlemesine ürün bilgileri ekler. Bu bilgileri görüntülenebilir **dosya özelliklerini** derleme için iletişim kutusu.|  
|**/ProductVersion:** `productversioninformation`|Çıktı derlemesine ürün sürümü ile ilgili bilgiler ekler. Biçim kısıtlamaları yoktur. Bu bilgileri görüntülenebilir **dosya özelliklerini** derleme için iletişim kutusu.|  
|**/PublicKey:** *dosya adı*|Elde edilen derlemeyi imzalamak için kullanılacak ortak anahtarı içeren dosyayı belirtir. Belirtirseniz **/keyfile:** veya **/keycontainer:** yerine seçeneği **/publickey:**, Tlbimp.exe ortak/özel anahtar çifti ile birlikte gelen ortak anahtarı oluşturur **/keyfile:** veya **/keycontainer:**. **/Publickey:** seçeneği destekler test anahtar ve gecikme imzalama. Dosya, Sn.exe tarafından üretilen biçimdedir. Daha fazla bilgi için bkz: **-p** içinde Sn.exe seçeneği [tanımlayıcı ad Aracı (Sn.exe)](sn-exe-strong-name-tool.md).|  
|**/ reference:** *dosya adı*|Geçerli tür kitaplığı dışında tanımlanmış tür başvurularını çözümlemek için kullanılacak derleme dosyasını belirtir. Belirtmezseniz, **/reference** seçeneğini Tlbimp.exe otomatik olarak yinelemeli tür kitaplığı başvuruları alınmakta olduğundan herhangi bir dış tür kitaplığı içeri aktarır. Belirtirseniz **/reference** seçeneği, aracı diğer tür kitaplıklarının alır önce başvurulan derlemeleri dış türlerinde çözmek çalışır.|  
|**/silence:** `warningnumber`|Belirtilen uyarının görüntülenmesini bastırır. Bu seçenek kullanılamaz **/sessiz**.|  
|**/silent**|Başarı iletilerinin görüntülenmesini bastırır. Bu seçenek kullanılamaz **/sessiz**.|  
|**/strictref**|Aracı ile belirtilen derlemeler geçerli derlemedeki tüm başvuruları çözemezseniz bir tür kitaplığı içeri aktarmaz **/reference** seçeneği veya kayıtlı birincil birlikte çalışma derlemeleri (PIA).|  
|**/strictref:nopia**|Aynı **/strictref**, ancak PIA yok sayar.|  
|**/sysarray**|COM Stili SafeArray yönetilen olarak almak için aracı belirtir <xref:System.Array> türü.|  
|**/tlbreference:** *dosya adı*|Kayıt defterine danışmadan tür kitaplığı başvurularını çözümlemek için kullanılacak tür kitaplığı dosyasını belirtir.<br /><br /> Bu seçeneğin bazı eski tür kitaplığı biçimlerini yüklenmediğini unutmayın.  Ancak, kayıt defteri veya geçerli dizin aracılığıyla, eski tür kitaplığı biçimlerini dolaylı olarak yine yükleyebilirsiniz.|  
|**/trademark:** `trademarkinformation`|Çıktı derlemesine ticari marka bilgileri ekler. Bu bilgileri görüntülenebilir **dosya özelliklerini** derleme için iletişim kutusu.|  
|**/ dönüştürme:** *transformname*|Belirtildiği gibi meta veri dönüşümleri *transformname* parametresi.<br /><br /> Belirtin **dispret** için *transformname* dönüştürme [Çıkış, retval] parametreleri arabirimlerindeki yalnızca gönderme (dispinterfaces) dönüş değerleri içine yöntemlerin parametresi.<br /><br /> Bu seçenek hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerindeki örneklere bakın.|  
|**/ unsafe**|Arabirimleri, .NET Framework güvenlik denetimleri olmadan üretir. Bu şekilde sunulan bir yöntemi çağırmak güvenlik riski oluşturabilir. Bu tür kodları ortaya çıkarmanın getireceği riskleri bilmiyorsanız bu seçeneği kullanmamalısınız.|  
|**/verbose**|Ayrıntılı modu belirtir; içeri aktarılan tür kitaplığı hakkında daha fazla bilgi görüntüler.|  
|**/VariantBoolFieldToBool**|Dönüştürür `VARIANT_BOOL` yapılara alanlarında <xref:System.Boolean>.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
> [!NOTE]
>  Tlbimp.exe için komut satırı seçenekleri büyük/küçük harfe duyarlı değildir ve herhangi bir sırayla sağlanabilir. Tek yapmanız gereken, onu benzersiz şekilde tanımlamak için seçeneği yeterince belirtmektir. Bu nedenle, **/n** eşdeğerdir **/nologo** ve **/OU:** *outfile.dll* eşdeğerdir **/out:**  *OutFile.dll*.  
  
## <a name="remarks"></a>Açıklamalar  
 Tlbimp.exe dönüştürmeleri tüm tür Kitaplığında bir defada gerçekleştirir. Tek bir tür kitaplığı içinde tanımlanmış bir tür alt kümesi için tür bilgileri oluştururken bu aracı kullanamazsınız.  
  
 Kullanışlı veya atamak gerekli görülür [tanımlayıcı adlar](../app-domains/strong-named-assemblies.md) derlemeler için. Bu nedenle, Tlbimp.exe tanımlayıcı adlarla adlandırılmış derlemeler oluşturmak için gereken bilgileri sağlayan seçenekler içerir. Her iki **/keyfile:** ve **/keycontainer:** seçenekleri derlemeleri tanımlayıcı adlar ile oturum açın. Bu nedenle, aynı anda bu seçeneklerden yalnızca birini sağlamak mantıklı olur.  
  
 Kullanarak birden çok başvuru derlemeleri belirtebilirsiniz **/reference** seçeneğini birden çok kez.  
  
 Birden fazla tür kitaplığı içeren bir modülden bir tür kitaplığını içeri aktarırken, isteğe bağlı olarak tür kitaplık dosyasına bir kaynak kimliği eklenebilir. Tlbimp.exe bu dosyayı yalnızca geçerli dizinde ise ya da tam yolunu belirtirseniz bulabilir. Bu konunun ilerleyen kısımlarındaki örneğe bakın.  
  
## <a name="examples"></a>Örnekler  
 Tür kitaplığı bulunan aşağıdaki komutu aynı ada sahip bir derleme oluşturur `myTest.tlb` ve .dll uzantısına sahip.  
  
```  
tlbimp myTest.tlb   
```  
  
 Aşağıdaki komutu adlı bir derleme oluşturur `myTest.dll`.  
  
```  
tlbimp  myTest.tlb  /out:myTest.dll  
```  
  
 Aşağıdaki komutu tarafından belirtilen tür kitaplığı aynı ada sahip bir derleme oluşturur `MyModule.dll\1` ve .dll uzantısına sahip. `MyModule.dll\1` Geçerli dizinde bulunması gerekir.  
  
```  
tlbimp MyModule.dll\1  
```  
  
 Aşağıdaki komutu adlı bir derleme oluşturur `myTestLib.dll` için tür kitaplığı `TestLib.dll`. **/Transform:dispret** seçeneği dönüştüren herhangi [out retval] yönetilen kitaplık dönüş değerleri türü kitaplığa dispinterfaces yöntemlere parametreleri.  
  
```  
tlbimp TestLib.dll /transform:dispret /out:myTestLib.dll  
```  
  
 Tür Kitaplığı `TestLib.dll`, önceki örnekte adlı bir görüntüleme arabirimi yöntemini içerir `SomeMethod` void döndürür ve [out retval] sahip parametre. Aşağıdaki kodu için girdi türü kitaplığı yöntemi imzası: `SomeMethod` içinde `TestLib.dll`.  
  
```  
void SomeMethod([out, retval] VARIANT_BOOL*);  
```  
  
 Belirtme **/transform:dispret** seçeneği neden dönüştürmek Tlbimp.exe `[out, retval]` parametresinin `SomeMethod` içine bir `bool` dönüş değeri. İçin Tlbimp.exe üreten yöntem imzası aşağıdadır `SomeMethod` yönetilen Kitaplığı'nda `myTestLib.dll` zaman **/transform:dispret** seçeneği belirtildi.  
  
```csharp  
bool SomeMethod();  
```  
  
 Yönetilen bir kitaplık için üretmek için Tlbimp.exe kullanıyorsanız `TestLib.dll` belirtmeden **/transform:dispret**, aracı için aşağıdaki yöntemi imzası üreten `SomeMethod` yönetilen Kitaplığı'nda `myTestLib.dll`.  
  
```csharp  
void SomeMethod(out bool x);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Araçlar](index.md)  
 [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](tlbexp-exe-type-library-exporter.md)  
 [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](../interop/importing-a-type-library-as-an-assembly.md)  
 [Derleme dönüştürme özeti için tür kitaplığı](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100))  
 [Ildasm.exe (IL Ayrıştırıcı)](ildasm-exe-il-disassembler.md)  
 [Sn.exe (Tanımlayıcı Ad Aracı)](sn-exe-strong-name-tool.md)  
 [Kesin Adlandırılmış Bütünleştirilmiş Kodlar](../app-domains/strong-named-assemblies.md)  
 [Tür kitaplıkları birlikte çalışma derlemeleri içe aktarmak için öznitelikler](https://msdn.microsoft.com/library/81e587b8-393f-43e1-9add-c4b05e65cbfd(v=vs.100))  
 [Komut İstemleri](developer-command-prompt-for-vs.md)
