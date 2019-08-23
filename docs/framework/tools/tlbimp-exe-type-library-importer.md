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
ms.openlocfilehash: f9c34b237655eb49b6a44c366586b3cabb5a684f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937971"
---
# <a name="tlbimpexe-type-library-importer"></a>Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)
Tür Kitaplığı İçeri Aktarma programı, COM tür kitaplığı içinde bulunan tür tanımlarını bir ortak dil çalışma zamanı derlemesi içindeki eşdeğer tanımlara dönüştürür. Tlbimp.exe'nin çıktısı, özgün tür kitaplığı içinde tanımlanan türler için çalışma zamanı meta verileri içeren bir ikili dosyadır (derleme). Bu dosyayı [ıldadsm. exe](ildasm-exe-il-disassembler.md)gibi araçlarla inceleyebilirsiniz.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
tlbimp tlbFile [options]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*Tlbdosya*|COM tür kitaplığı içeren herhangi bir dosyanın adı.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/asmversion:** *SürümNumarası*|Üretilecek derlemenin sürüm numarasını belirtir. *VersionNumber* ' i *ana. Minor. Build. Revision*biçiminde belirtin.|  
|**/Company:** `companyinformation`|Şirket bilgilerini çıktı derlemesine ekler.|  
|**/telif hakkı:** `copyrightinformation`|Çıktı derlemesine telif hakkı bilgileri ekler. Bu bilgiler, derleme için **dosya özellikleri** iletişim kutusunda görüntülenebilir.|  
|**/delaysign**|Elde edilen ve tanımlayıcı bir ada sahip olan derlemeyi gecikmeli imzalama yöntemiyle imzalamak için kullanılacak Tlbimp.exe'yi belirtir. Bu seçeneği **/keycontainer:** , **/keyfile:** , ya da **/publickey:** seçeneğiyle belirtmeniz gerekir. Gecikmeli imzalama işlemi hakkında daha fazla bilgi için bkz. [bir derlemeyi IMZALAMAYı geciktirme](../app-domains/delay-sign-assembly.md).|  
|**/ Help**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/keycontainer:** *ContainerName*|Sonuç bütünleştirilmiş kodu, *ContainerName*tarafından belirtilen anahtar kapsayıcısında bulunan ortak/özel anahtar çiftini kullanarak tanımlayıcı bir adla imzalar.|  
|**/keyfile:** *dosya adı*|Sonuçta ortaya çıkan derlemeyi, yayımcının *dosya adında*bulunan resmi ortak/özel anahtar çiftini kullanarak tanımlayıcı bir adla imzalar.|  
|**/MACHINE:** `machinetype`|Belirtilen makine türünü (mikro işlemci) hedefleyen bir derleme oluşturur. Desteklenen makine türleri: x86, x64, Itanium ve Belirsiz.|  
|**/Namespace:** *ad alanı*|Derlemenin oluşturulacağı ad alanını belirtir.|  
|**/NoClassMembers**|Tlbimp.exe'nin sınıflara üye eklemesini önler. Bu, olası bir <xref:System.TypeLoadException>olasılık olduğunu önler.|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/Out:** *dosya adı*|İçine meta veri tanımlarının yazılacağı çıktı dosyasının, derlemenin ve ad alanının adını belirtir. Tür kitaplığı, derlemenin ad alanını açıkça denetleyen arabirim tanım dili (IDL) özel özniteliğini belirtiyorsa **/Out** seçeneğinin derlemenin ad alanı üzerinde hiçbir etkisi yoktur. Bu seçeneği belirtmezseniz, Tlbimp.exe, girdi dosyasında tanımlanan asıl tür kitaplığıyla aynı ada sahip bir dosyaya meta verileri yazar ve ona bir .dll uzantısı atar. Çıktı dosyasının adı girdi dosyasının adıyla aynı ise, araç tür kitaplığı üzerine yazılmasını engellemek için bir hata üretir.|  
|**/birincil**|Belirtilen tür kitaplığı için bir birincil birlikte çalışma derlemesi oluşturur. Derlemeyi tür kitaplığı yayıncısının oluşturduğunu belirten bilgiler derlemeye eklenir. Birincil birlikte çalışma derlemesi belirterek, bir yayıncının derlemesini, Tlbimp.exe kullanarak tür kitaplığından oluşturulan diğer derlemelerden ayırt edersiniz. **/Primary** seçeneğini yalnızca Tlbimp. exe ile içeri aktardığınız tür kitaplığının yayımcısıdır kullanmanız gerekir. Bir birincil birlikte çalışma derlemesini [tanımlayıcı bir adla](../app-domains/strong-named-assemblies.md)imzalamanız gerektiğini unutmayın. Daha fazla bilgi için bkz. [birincil birlikte çalışma derlemeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).|  
|**/Ürün:** `productinformation`|Çıktı derlemesine ürün bilgileri ekler. Bu bilgiler, derleme için **dosya özellikleri** iletişim kutusunda görüntülenebilir.|  
|**/ProductVersion:** `productversioninformation`|Çıktı derlemesine ürün sürümü ile ilgili bilgiler ekler. Biçim kısıtlamaları yoktur. Bu bilgiler, derleme için **dosya özellikleri** iletişim kutusunda görüntülenebilir.|  
|**/publickey:** *dosya adı*|Elde edilen derlemeyi imzalamak için kullanılacak ortak anahtarı içeren dosyayı belirtir. /PublicKey: ' nin yerine/keyfile: veya **/keycontainer** : seçeneğinibelirtirseniz, Tlbimp. exe, **/keyfile:** veya **/keycontainer:** ile sağlanan ortak/özel anahtar çiftinden ortak anahtar oluşturur. **/Publickey:** seçeneği test anahtarını ve Gecikmeli imzalama senaryolarını destekler. Dosya, Sn.exe tarafından üretilen biçimdedir. Daha fazla bilgi için, tanımlayıcı ad aracında sn. exe ' nin **-p** seçeneğine [(sn. exe)](sn-exe-strong-name-tool.md)bakın.|  
|**/Reference:** *dosya adı*|Geçerli tür kitaplığı dışında tanımlanmış tür başvurularını çözümlemek için kullanılacak derleme dosyasını belirtir. **/Reference** seçeneğini belirtmezseniz, Tlbimp. exe otomatik olarak tür kitaplığının içeri aktardığı herhangi bir dış tür kitaplığını içeri aktarır. **/Reference** seçeneğini belirtirseniz, araç diğer tür kitaplıklarını içeri aktarmadan önce başvurulan derlemelerdeki dış türleri çözümlemeye çalışır.|  
|**/sessizlik:** `warningnumber`|Belirtilen uyarının görüntülenmesini bastırır. Bu seçenek **/Silent**ile kullanılamaz.|  
|**/silent**|Başarı iletilerinin görüntülenmesini bastırır. Bu seçenek **/sessizlik**ile kullanılamaz.|  
|**/strictref**|Araç geçerli derleme içindeki tüm başvuruları, **/Reference** seçeneğiyle belirtilen derlemeleri veya kayıtlı birincil birlikte çalışma derlemelerini (PIA 'lar) çözümleyemezse, bir tür kitaplığını içeri aktarmaz.|  
|**/strictref: nopıa**|**/Strictref**ile aynıdır, ancak PIA 'leri yoksayar.|  
|**/sysarray**|Bir com stili SAFEARRAY 'i yönetilen <xref:System.Array> bir tür olarak içeri aktarmak için araca belirtir.|  
|**/tlbreference:** *dosya adı*|Kayıt defterine danışmadan tür kitaplığı başvurularını çözümlemek için kullanılacak tür kitaplığı dosyasını belirtir.<br /><br /> Bu seçeneğin bazı eski tür kitaplığı biçimlerini yüklenmediğini unutmayın.  Ancak, kayıt defteri veya geçerli dizin aracılığıyla, eski tür kitaplığı biçimlerini dolaylı olarak yine yükleyebilirsiniz.|  
|**/ticari marka:** `trademarkinformation`|Çıktı derlemesine ticari marka bilgileri ekler. Bu bilgiler, derleme için **dosya özellikleri** iletişim kutusunda görüntülenebilir.|  
|**/Transform:** *transformname*|*Transformname* parametresi tarafından belirtilen meta verileri dönüştürür.<br /><br /> Yalnızca dağıtım arabirimlerinde (dispınterfaces) yöntemlerin [Out, retval] parametrelerini dönüş değerlerine dönüştürmek için *transformname* parametresinin **dispret** değerini belirtin.<br /><br /> Bu seçenek hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerindeki örneklere bakın.|  
|**/unsafe**|Arabirimleri, .NET Framework güvenlik denetimleri olmadan üretir. Bu şekilde sunulan bir yöntemi çağırmak güvenlik riski oluşturabilir. Bu tür kodları ortaya çıkarmanın getireceği riskleri bilmiyorsanız bu seçeneği kullanmamalısınız.|  
|**/verbose**|Ayrıntılı modu belirtir; içeri aktarılan tür kitaplığı hakkında daha fazla bilgi görüntüler.|  
|**/VariantBoolFieldToBool**|Yapılardaki alanları öğesine `VARIANT_BOOL` <xref:System.Boolean>dönüştürür.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
> [!NOTE]
> Tlbimp.exe için komut satırı seçenekleri büyük/küçük harfe duyarlı değildir ve herhangi bir sırayla sağlanabilir. Tek yapmanız gereken, onu benzersiz şekilde tanımlamak için seçeneği yeterince belirtmektir. Bu nedenle, **/n** **/nologo** ve **/OU** ile eşdeğerdir: *çıkışdosyası. dll* **/Out:** *çıkışdosyası. dll*ile eşdeğerdir.  
  
## <a name="remarks"></a>Açıklamalar  
 Tlbimp.exe dönüştürmeleri tüm tür Kitaplığında bir defada gerçekleştirir. Tek bir tür kitaplığı içinde tanımlanmış bir tür alt kümesi için tür bilgileri oluştururken bu aracı kullanamazsınız.  
  
 Derlemelere [tanımlayıcı adlar](../app-domains/strong-named-assemblies.md) atayabilmesi genellikle yararlı veya gereklidir. Bu nedenle, Tlbimp.exe tanımlayıcı adlarla adlandırılmış derlemeler oluşturmak için gereken bilgileri sağlayan seçenekler içerir. Hem **/keyfile:** hem de **/keycontainer:** seçenekler derlemeleri tanımlayıcı adlarla imzalar. Bu nedenle, aynı anda bu seçeneklerden yalnızca birini sağlamak mantıklı olur.  
  
 **/Reference** seçeneğini birden çok kez kullanarak birden çok başvuru derlemesi belirleyebilirsiniz.
 
 Tlbimp. exe ' nin derlemeler üretme yöntemi nedeniyle, bir derlemeyi farklı `mscorlib` bir sürüme yeniden hedeflemeniz mümkün değildir. Örneğin, .NET Framework 2,0 ' i hedefleyen bir derleme oluşturmak isterseniz, .NET Framework 2.0/3.0/3.5 SDK ile gönderilen Tlbimp. exe ' nin kullanılması gerekir. .NET Framework 4. x ' i hedeflemek için, bir .NET Framework 4. x SDK ile gönderilen Tlbimp. exe kullanılmalı.
 
 Birden fazla tür kitaplığı içeren bir modülden bir tür kitaplığını içeri aktarırken, isteğe bağlı olarak tür kitaplık dosyasına bir kaynak kimliği eklenebilir. Tlbimp.exe bu dosyayı yalnızca geçerli dizinde ise ya da tam yolunu belirtirseniz bulabilir. Bu konunun ilerleyen kısımlarındaki örneğe bakın.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut,. dll uzantısıyla ve ' de `myTest.tlb` bulunan tür kitaplığıyla aynı ada sahip bir derleme oluşturur.  
  
```  
tlbimp myTest.tlb   
```  
  
 Aşağıdaki komut, adında `myTest.dll`bir derleme oluşturur.  
  
```  
tlbimp  myTest.tlb  /out:myTest.dll  
```  
  
 Aşağıdaki komut,. dll uzantısıyla ve tarafından `MyModule.dll\1` belirtilen tür kitaplığıyla aynı ada sahip bir derleme oluşturur. `MyModule.dll\1`geçerli dizinde bulunmalıdır.  
  
```  
tlbimp MyModule.dll\1  
```  
  
 Aşağıdaki komut, tür kitaplığının `myTestLib.dll` `TestLib.dll`adına sahip bir derleme oluşturur. **/Transform: dispret** seçeneği, tür kitaplığındaki dispınterfaces üzerinde bulunan tüm [Out, retval] parametrelerini yönetilen kitaplıktaki dönüş değerlerine dönüştürür.  
  
```  
tlbimp TestLib.dll /transform:dispret /out:myTestLib.dll  
```  
  
 Yukarıdaki örnekteki tür `TestLib.dll`kitaplığı, void döndüren ve bir [Out, retval] parametresine `SomeMethod` sahip adlı bir dispınterface yöntemi içerir. Aşağıdaki kod, içindeki `SomeMethod` `TestLib.dll`için giriş türü kitaplığı Yöntem imzasıdır.  
  
```  
void SomeMethod([out, retval] VARIANT_BOOL*);  
```  
  
 **/Transform: dispret** seçeneğinin belirtilmesi, Tlbimp. exe ' nin `[out, retval]` `SomeMethod` parametresini bir `bool` dönüş değerine dönüştürmesine neden olur. Aşağıda, **/Transform: dispret** seçeneği belirtildiğinde, Tlbimp `SomeMethod` . exe ' nin `myTestLib.dll` yönetilen kitaplıkta için ürettiği Yöntem imzası verilmiştir.  
  
```csharp  
bool SomeMethod();  
```  
  
 `TestLib.dll` **/Transform: dispret**belirtmeden için bir yönetilen kitaplık oluşturmak üzere Tlbimp. exe ' yi kullanırsanız, araç yönetilen kitaplıkta `SomeMethod` `myTestLib.dll`için aşağıdaki yöntem imzasını üretir.  
  
```csharp  
void SomeMethod(out bool x);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](tlbexp-exe-type-library-exporter.md)
- [Tür Kitaplığını Bütünleştirilmiş Kod Olarak İçeri Aktarma](../interop/importing-a-type-library-as-an-assembly.md)
- [Tür kitaplığını derlemeye dönüştürme Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Ildasm.exe (IL Ayrıştırıcı)](ildasm-exe-il-disassembler.md)
- [Sn.exe (Tanımlayıcı Ad Aracı)](sn-exe-strong-name-tool.md)
- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar](../app-domains/strong-named-assemblies.md)
- [Tür kitaplıklarını birlikte çalışma derlemelerine Içeri aktarmaya yönelik öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/y6a7ak23(v=vs.100))
- [Komut İstemleri](developer-command-prompt-for-vs.md)
