---
title: Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)
ms.date: 03/30/2017
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
ms.openlocfilehash: 4f9741944dcf8a5fcc05c169a1c3c3f679902474
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859675"
---
# <a name="tlbimpexe-type-library-importer"></a>Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)
Tür Kitaplığı İçeri Aktarma programı, COM tür kitaplığı içinde bulunan tür tanımlarını bir ortak dil çalışma zamanı derlemesi içindeki eşdeğer tanımlara dönüştürür. Tlbimp.exe'nin çıktısı, özgün tür kitaplığı içinde tanımlanan türler için çalışma zamanı meta verileri içeren bir ikili dosyadır (derleme). Gibi araçlarla bu dosyayı inceleyebilirsiniz [Ildasm.exe](ildasm-exe-il-disassembler.md).  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici Komut İstemi'ni kullanın. Daha fazla bilgi için [komut istemleri](developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
tlbimp tlbFile [options]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*tlbFile*|COM tür kitaplığı içeren herhangi bir dosyanın adı.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/asmversion:** *versionnumber*|Üretilecek derlemenin sürüm numarasını belirtir. Belirtin *versionnumber* biçimde *major.minor.build.revision*.|  
|**/Company:** `companyinformation`|Şirket bilgilerini çıktı derlemesine ekler.|  
|**/Copyright:** `copyrightinformation`|Çıktı derlemesine telif hakkı bilgileri ekler. Bu bilgiler görüntülenebilir **dosya özelliklerini** derleme için iletişim kutusu.|  
|**/delaysign**|Elde edilen ve tanımlayıcı bir ada sahip olan derlemeyi gecikmeli imzalama yöntemiyle imzalamak için kullanılacak Tlbimp.exe'yi belirtir. Bu seçeneği ile birlikte belirtmelisiniz **/keycontainer:** , **/keyfile:** , veya **/publickey:** seçeneği. Gecikmeli imzalama işlemi hakkında daha fazla bilgi için bkz. [derlemeyi imzalamayı geciktirme](../app-domains/delay-sign-assembly.md).|  
|**/ Help**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/ keycontainer:** *containername*|Oluşturulan derleme tarafından belirtilen anahtar kapsayıcısında bulunan ortak/özel anahtar çiftini kullanarak tanımlayıcı bir adla imzalar *containername*.|  
|**/ keyfile:** *dosya adı*|Elde edilen derlemeyi bulunan yayımcının resmi ortak/özel anahtar çiftini kullanarak tanımlayıcı bir adla imzalar *filename*.|  
|**/ Machine:** `machinetype`|Belirtilen makine türünü (mikro işlemci) hedefleyen bir derleme oluşturur. Desteklenen makine türleri: x86, x64, Itanium ve Belirsiz.|  
|**/ Namespace:** *ad alanı*|Derlemenin oluşturulacağı ad alanını belirtir.|  
|**/noclassmembers**|Tlbimp.exe'nin sınıflara üye eklemesini önler. Bu olası önler <xref:System.TypeLoadException>.|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/ out:** *dosya adı*|İçine meta veri tanımlarının yazılacağı çıktı dosyasının, derlemenin ve ad alanının adını belirtir. **/Out** seçeneği varsa derlemenin ad alanı üzerinde hiçbir etkisi açıkça derlemenin ad alanını denetleyen arabirim tanımlama dili (IDL) özel özniteliği tür kitaplığını belirtir. Bu seçeneği belirtmezseniz, Tlbimp.exe, girdi dosyasında tanımlanan asıl tür kitaplığıyla aynı ada sahip bir dosyaya meta verileri yazar ve ona bir .dll uzantısı atar. Çıktı dosyasının adı girdi dosyasının adıyla aynı ise, araç tür kitaplığı üzerine yazılmasını engellemek için bir hata üretir.|  
|**/ birincil**|Belirtilen tür kitaplığı için bir birincil birlikte çalışma derlemesi oluşturur. Derlemeyi tür kitaplığı yayıncısının oluşturduğunu belirten bilgiler derlemeye eklenir. Birincil birlikte çalışma derlemesi belirterek, bir yayıncının derlemesini, Tlbimp.exe kullanarak tür kitaplığından oluşturulan diğer derlemelerden ayırt edersiniz. Yalnızca kullanmalısınız **/birincil** Tlbimp.exe ile içeri aktardığınız tür kitaplığının yayıncısı iseniz. Bir birincil birlikte çalışma derlemesi ile imzalamanız gerektiğini unutmayın bir [tanımlayıcı ad](../app-domains/strong-named-assemblies.md). Daha fazla bilgi için [birincil birlikte çalışma derlemelerini](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).|  
|**/Product:** `productinformation`|Çıktı derlemesine ürün bilgileri ekler. Bu bilgiler görüntülenebilir **dosya özelliklerini** derleme için iletişim kutusu.|  
|**/ProductVersion:** `productversioninformation`|Çıktı derlemesine ürün sürümü ile ilgili bilgiler ekler. Biçim kısıtlamaları yoktur. Bu bilgiler görüntülenebilir **dosya özelliklerini** derleme için iletişim kutusu.|  
|**/PublicKey:** *dosya adı*|Elde edilen derlemeyi imzalamak için kullanılacak ortak anahtarı içeren dosyayı belirtir. Belirtirseniz **/keyfile:** veya **/keycontainer:** yerine seçeneği **/publickey:** , Tlbimp.exe ile sağlanan ortak/özel anahtar çifti öğesinden ortak anahtarı oluşturur **/keyfile:** veya **/keycontainer:** . **/Publickey:** test anahtarını ve Gecikmeli imzalama senaryolarını seçeneği destekler. Dosya, Sn.exe tarafından üretilen biçimdedir. Daha fazla bilgi için **-p** seçeneği sn.exe [tanımlayıcı ad Aracı (Sn.exe)](sn-exe-strong-name-tool.md).|  
|**/ reference:** *dosya adı*|Geçerli tür kitaplığı dışında tanımlanmış tür başvurularını çözümlemek için kullanılacak derleme dosyasını belirtir. Siz belirtmezseniz **/reference** seçeneği, Tlbimp.exe otomatik olarak yinelemeli tür kitaplığı içeri aktarılan başvurular herhangi bir dış tür kitaplığı içeri aktarır. Belirtirseniz **/reference** seçeneği, aracı, diğer tür kitaplıklarını içeri aktarmadan önce başvurulan derlemelerdeki dış türleri çözümlemeye çalışır.|  
|**/silence:** `warningnumber`|Belirtilen uyarının görüntülenmesini bastırır. Bu seçenek kullanılamaz **/silent**.|  
|**/silent**|Başarı iletilerinin görüntülenmesini bastırır. Bu seçenek kullanılamaz **/sessiz**.|  
|**/strictref**|Araç geçerli derlemedeki, belirtilen derlemelerdeki tüm başvuruları çözümleyemezse bir tür kitaplığını içeri aktarmaz **/reference** seçeneği veya kayıtlı birincil birlikte çalışma derlemeleri (PIA).|  
|**/strictref:nopia**|Aynı **/strictref**, ancak PIA'ların yoksayar.|  
|**/sysarray**|Bir COM Stili SAFEARRAY'i yönetilen olarak içeri aktaracağını belirtir <xref:System.Array> türü.|  
|**/tlbreference:** *dosya adı*|Kayıt defterine danışmadan tür kitaplığı başvurularını çözümlemek için kullanılacak tür kitaplığı dosyasını belirtir.<br /><br /> Bu seçeneğin bazı eski tür kitaplığı biçimlerini yüklenmediğini unutmayın.  Ancak, kayıt defteri veya geçerli dizin aracılığıyla, eski tür kitaplığı biçimlerini dolaylı olarak yine yükleyebilirsiniz.|  
|**/trademark:** `trademarkinformation`|Çıktı derlemesine ticari marka bilgileri ekler. Bu bilgiler görüntülenebilir **dosya özelliklerini** derleme için iletişim kutusu.|  
|**/ dönüştürme:** *transformname*|Tarafından belirtilen meta veri dönüşümleri *transformname* parametresi.<br /><br /> Belirtin **dispret** için *transformname* yöntemlerin yalnızca gönderme (görüntüleme arabirimleri) dönüş değerlerine dönüştürme [out, retval] parametrelerini parametre.<br /><br /> Bu seçenek hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerindeki örneklere bakın.|  
|**/ unsafe**|Arabirimleri, .NET Framework güvenlik denetimleri olmadan üretir. Bu şekilde sunulan bir yöntemi çağırmak güvenlik riski oluşturabilir. Bu tür kodları ortaya çıkarmanın getireceği riskleri bilmiyorsanız bu seçeneği kullanmamalısınız.|  
|**/verbose**|Ayrıntılı modu belirtir; içeri aktarılan tür kitaplığı hakkında daha fazla bilgi görüntüler.|  
|**/VariantBoolFieldToBool**|Dönüştürür `VARIANT_BOOL` yapılarını alanlarında <xref:System.Boolean>.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
> [!NOTE]
>  Tlbimp.exe için komut satırı seçenekleri büyük/küçük harfe duyarlı değildir ve herhangi bir sırayla sağlanabilir. Tek yapmanız gereken, onu benzersiz şekilde tanımlamak için seçeneği yeterince belirtmektir. Bu nedenle, **/n** eşdeğerdir **/nologo** ve **/OU:** *outfile.dll* eşdeğerdir **/out:**  *OutFile.dll*.  
  
## <a name="remarks"></a>Açıklamalar  
 Tlbimp.exe dönüştürmeleri tüm tür Kitaplığında bir defada gerçekleştirir. Tek bir tür kitaplığı içinde tanımlanmış bir tür alt kümesi için tür bilgileri oluştururken bu aracı kullanamazsınız.  
  
 Yararlı veya gereklidir atayabilmek genellikle [güçlü adlar](../app-domains/strong-named-assemblies.md) derlemelere. Bu nedenle, Tlbimp.exe tanımlayıcı adlarla adlandırılmış derlemeler oluşturmak için gereken bilgileri sağlayan seçenekler içerir. Her iki **/keyfile:** ve **/keycontainer:** seçenekleri derlemeleri tanımlayıcı adlarla oturum açın. Bu nedenle, aynı anda bu seçeneklerden yalnızca birini sağlamak mantıklı olur.  
  
 Kullanarak, pek çok başvuru derlemesi belirtebilirsiniz **/reference** seçeneğini birden çok kez.
 
 Tlbimp.exe derlemeleri üretir yöntemi nedeniyle, farklı bir derleme yeniden hedeflemek mümkün değildir `mscorlib` sürümü. Örneğin, .NET Framework 2. 0'ı hedefleyen bir derleme oluşturmak isterseniz, Tlbimp.exe SDK kullanılan .NET Framework 2.0/3.0/3.5 ile birlikte gelir. .NET Framework hedeflemek için bir .NET Framework 4.x, Tlbimp.exe sevk 4.x SDK'sı kullanılması gerekir.
 
 Birden fazla tür kitaplığı içeren bir modülden bir tür kitaplığını içeri aktarırken, isteğe bağlı olarak tür kitaplık dosyasına bir kaynak kimliği eklenebilir. Tlbimp.exe bu dosyayı yalnızca geçerli dizinde ise ya da tam yolunu belirtirseniz bulabilir. Bu konunun ilerleyen kısımlarındaki örneğe bakın.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut içinde bulunan tür kitaplığıyla aynı ada sahip bir derleme oluşturur `myTest.tlb` .dll uzantısıyla ve.  
  
```  
tlbimp myTest.tlb   
```  
  
 Aşağıdaki komutu ada sahip bir derleme oluşturur `myTest.dll`.  
  
```  
tlbimp  myTest.tlb  /out:myTest.dll  
```  
  
 Aşağıdaki komutu tarafından belirtilen tür kitaplığıyla aynı ada sahip bir derleme oluşturur `MyModule.dll\1` .dll uzantısıyla ve. `MyModule.dll\1` Geçerli dizinde bulunmalıdır.  
  
```  
tlbimp MyModule.dll\1  
```  
  
 Aşağıdaki komutu ada sahip bir derleme oluşturur `myTestLib.dll` tür kitaplığı için `TestLib.dll`. **/Transform:dispret** seçeneği dönüştüren bir [out, retval] parametrelerini yönetilen kitaplıkta dönüş değerlerine tür kitaplığındaki görüntü arabirimlerinde bulunan yöntemlerin.  
  
```  
tlbimp TestLib.dll /transform:dispret /out:myTestLib.dll  
```  
  
 Tür kitaplığını `TestLib.dll`, önceki örnekte adlı bir görüntü arabirimi yöntemi içerir `SomeMethod` , void döndüren ve sahip bir [out, retval] parametresi. Aşağıdaki kodu için giriş türü kitaplığı yöntem imzasıdır olan `SomeMethod` içinde `TestLib.dll`.  
  
```  
void SomeMethod([out, retval] VARIANT_BOOL*);  
```  
  
 Belirtme **/transform:dispret** seçeneği neden olur, Tlbimp.exe'nin `[out, retval]` parametresinin `SomeMethod` içine bir `bool` değeri döndürür. Tlbimp.exe için ürettiği yöntem imzası verilmiştir `SomeMethod` yönetilen kitaplıkta `myTestLib.dll` olduğunda **/transform:dispret** seçeneği belirtildi.  
  
```csharp  
bool SomeMethod();  
```  
  
 Tlbimp.exe'nin yönetilen kitaplık oluşturmak için kullanırsanız `TestLib.dll` belirtmeden **/transform:dispret**, aracı için aşağıdaki yöntem imzasını üretir `SomeMethod` yönetilen kitaplıkta `myTestLib.dll`.  
  
```csharp  
void SomeMethod(out bool x);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](tlbexp-exe-type-library-exporter.md)
- [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](../interop/importing-a-type-library-as-an-assembly.md)
- [Tür kitaplığını derlemeye dönüştürme özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Ildasm.exe (IL Ayrıştırıcı)](ildasm-exe-il-disassembler.md)
- [Sn.exe (Tanımlayıcı Ad Aracı)](sn-exe-strong-name-tool.md)
- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar](../app-domains/strong-named-assemblies.md)
- [Tür kitaplıklarını birlikte çalışma derlemelerine içeri aktarma için öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/y6a7ak23(v=vs.100))
- [Komut İstemleri](developer-command-prompt-for-vs.md)
