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
ms.openlocfilehash: d942378888b06049022188c75456f438d4b187e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180241"
---
# <a name="tlbimpexe-type-library-importer"></a>Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)
Tür Kitaplığı İçeri Aktarma programı, COM tür kitaplığı içinde bulunan tür tanımlarını bir ortak dil çalışma zamanı derlemesi içindeki eşdeğer tanımlara dönüştürür. Tlbimp.exe'nin çıktısı, özgün tür kitaplığı içinde tanımlanan türler için çalışma zamanı meta verileri içeren bir ikili dosyadır (derleme). Bu dosyayı [Ildasm.exe](ildasm-exe-il-disassembler.md)gibi araçlarla inceleyebilirsiniz.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
tlbimp tlbFile [options]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*tlbDosya*|COM tür kitaplığı içeren herhangi bir dosyanın adı.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/asmversion:** *sürüm numarası*|Üretilecek derlemenin sürüm numarasını belirtir. sürüm *numarasını* *major.minor.build.revision*biçiminde belirtin.|  
|**/şirket:**`companyinformation`|Şirket bilgilerini çıktı derlemesine ekler.|  
|**/telif hakkı:**`copyrightinformation`|Çıktı derlemesine telif hakkı bilgileri ekler. Bu bilgiler, derleme için **Dosya Özellikleri** iletişim kutusunda görüntülenebilir.|  
|**/delaysign**|Elde edilen ve tanımlayıcı bir ada sahip olan derlemeyi gecikmeli imzalama yöntemiyle imzalamak için kullanılacak Tlbimp.exe'yi belirtir. Bu seçeneği **/keycontainer:**, **/keyfile:**, veya **/publickey:** seçeneği yle belirtmeniz gerekir. Gecikmiş imzalama işlemi hakkında daha fazla bilgi için, [Bir Meclis'i İmzalamayı Geciktirme'ye](../../standard/assembly/delay-sign.md)bakın.|  
|**/yardım**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/keycontainer:** *konteyner adı*|*Konteyner adı*ile belirtilen anahtar kapsayıcısında bulunan ortak/özel anahtar çiftini kullanarak ortaya çıkan derlemeyi güçlü bir adla imzalar.|  
|**/keyfile:** *dosya adı*|*Dosya adında*bulunan yayımcının resmi ortak/özel anahtar çiftini kullanarak ortaya çıkan derlemeyi güçlü bir adla imzalar.|  
|**/makine:**`machinetype`|Belirtilen makine türünü (mikro işlemci) hedefleyen bir derleme oluşturur. Desteklenen makine türleri: x86, x64, Itanium ve Belirsiz.|  
|**/namespace:** *ad alanı*|Derlemenin oluşturulacağı ad alanını belirtir.|  
|**/noclassmembers**|Tlbimp.exe'nin sınıflara üye eklemesini önler. Bu bir potansiyel <xref:System.TypeLoadException>önler.|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/out:** *dosya adı*|İçine meta veri tanımlarının yazılacağı çıktı dosyasının, derlemenin ve ad alanının adını belirtir. Tür kitaplığı, derlemenin ad alanını açıkça kontrol eden Arabirim Tanımı Dili (IDL) özel özniteliğini belirtmişse, **/out** seçeneğinin derlemenin ad alanı üzerinde hiçbir etkisi yoktur. Bu seçeneği belirtmezseniz, Tlbimp.exe, girdi dosyasında tanımlanan asıl tür kitaplığıyla aynı ada sahip bir dosyaya meta verileri yazar ve ona bir .dll uzantısı atar. Çıktı dosyasının adı girdi dosyasının adıyla aynı ise, araç tür kitaplığı üzerine yazılmasını engellemek için bir hata üretir.|  
|**/birincil**|Belirtilen tür kitaplığı için bir birincil birlikte çalışma derlemesi oluşturur. Derlemeyi tür kitaplığı yayıncısının oluşturduğunu belirten bilgiler derlemeye eklenir. Birincil birlikte çalışma derlemesi belirterek, bir yayıncının derlemesini, Tlbimp.exe kullanarak tür kitaplığından oluşturulan diğer derlemelerden ayırt edersiniz. **/birincil** seçeneğini yalnızca Tlbimp.exe ile içe aktardığınız tür kitaplığınyayımcısıysanız kullanmalısınız. Güçlü bir [ada](../../standard/assembly/strong-named.md)sahip birincil interop derlemesi imzalamanız gerektiğini unutmayın. Daha fazla bilgi için [Birincil Interop Montajları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100))bakın.|  
|**/ürün:**`productinformation`|Çıktı derlemesine ürün bilgileri ekler. Bu bilgiler, derleme için **Dosya Özellikleri** iletişim kutusunda görüntülenebilir.|  
|**/productversion:**`productversioninformation`|Çıktı derlemesine ürün sürümü ile ilgili bilgiler ekler. Biçim kısıtlamaları yoktur. Bu bilgiler, derleme için **Dosya Özellikleri** iletişim kutusunda görüntülenebilir.|  
|**/publickey:** *dosya adı*|Elde edilen derlemeyi imzalamak için kullanılacak ortak anahtarı içeren dosyayı belirtir. **/keyfile:** veya **/keycontainer:** seçeneği yerine **/publickey:**, Tlbimp.exe **/keyfile** ile birlikte verilen ortak/özel anahtar çiftinden ortak anahtarı oluşturur: veya **/keycontainer:**. **/publickey:** seçeneği test anahtarı nı destekler ve imzalama senaryolarını geciktirir. Dosya, Sn.exe tarafından üretilen biçimdedir. Daha fazla bilgi için [Güçlü Ad Aracı 'da (Sn.exe)](sn-exe-strong-name-tool.md)Sn.exe'nin **-p** seçeneğine bakın.|  
|**/reference:** *dosya adı*|Geçerli tür kitaplığı dışında tanımlanmış tür başvurularını çözümlemek için kullanılacak derleme dosyasını belirtir. **/başvuru** seçeneğini belirtmezseniz, Tlbimp.exe, dış yazı kitaplığını n için içe aktardığı dış tür kitaplığını otomatik olarak yineler. **/başvuru** seçeneğini belirtirseniz, araç diğer tür kitaplıklarını içeri almadan önce başvurulan derlemelerde dış türleri çözümlemeye çalışır.|  
|**/sessizlik:**`warningnumber`|Belirtilen uyarının görüntülenmesini bastırır. Bu seçenek **/silent**ile kullanılamaz.|  
|**/silent**|Başarı iletilerinin görüntülenmesini bastırır. Bu seçenek **/silence**ile kullanılamaz.|  
|**/strictref**|Araç geçerli derlemedeki tüm başvuruları, **/reference** seçeneğiyle belirtilen derlemeleri veya kayıtlı birincil interop derlemelerini (PIA) çözemiyorsa, tür kitaplığı almaz.|  
|**/strictref:nopia**|**/strictref**ile aynı , ancak PIA'ları yok sayıyor.|  
|**/sysarray**|Yönetilen bir <xref:System.Array> tür olarak com stili SafeArray almak için araca belirtir.|  
|**/tlbreference:** *dosya adı*|Kayıt defterine danışmadan tür kitaplığı başvurularını çözümlemek için kullanılacak tür kitaplığı dosyasını belirtir.<br /><br /> Bu seçeneğin bazı eski tür kitaplığı biçimlerini yüklenmediğini unutmayın.  Ancak, kayıt defteri veya geçerli dizin aracılığıyla, eski tür kitaplığı biçimlerini dolaylı olarak yine yükleyebilirsiniz.|  
|**/ticari marka:**`trademarkinformation`|Çıktı derlemesine ticari marka bilgileri ekler. Bu bilgiler, derleme için **Dosya Özellikleri** iletişim kutusunda görüntülenebilir.|  
|**/transform:** *transformname*|Dönüştürme adı parametresi tarafından belirtildiği gibi meta verileri *dönüştürür.*<br /><br /> Yalnızca gönderme arabirimlerindeki (dispinterfaces) yöntemlerin [çıkış, retval] parametrelerini return değerlerine dönüştürmek **için** *transformname* parametresini belirtin.<br /><br /> Bu seçenek hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerindeki örneklere bakın.|  
|**/güvensiz**|Arabirimleri, .NET Framework güvenlik denetimleri olmadan üretir. Bu şekilde sunulan bir yöntemi çağırmak güvenlik riski oluşturabilir. Bu tür kodları ortaya çıkarmanın getireceği riskleri bilmiyorsanız bu seçeneği kullanmamalısınız.|  
|**/ayrıntılı**|Ayrıntılı modu belirtir; içeri aktarılan tür kitaplığı hakkında daha fazla bilgi görüntüler.|  
|**/VariantBoolFieldToBool**|Yapılardaki `VARIANT_BOOL` alanları <xref:System.Boolean>.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
> [!NOTE]
> Tlbimp.exe için komut satırı seçenekleri büyük/küçük harfe duyarlı değildir ve herhangi bir sırayla sağlanabilir. Tek yapmanız gereken, onu benzersiz şekilde tanımlamak için seçeneği yeterince belirtmektir. Bu nedenle, **/n** **/nologo** ve **/ou:** *outfile.dll* eşdeğerdir **/out:** *outfile.dll*.  
  
## <a name="remarks"></a>Açıklamalar  
 Tlbimp.exe dönüştürmeleri tüm tür Kitaplığında bir defada gerçekleştirir. Tek bir tür kitaplığı içinde tanımlanmış bir tür alt kümesi için tür bilgileri oluştururken bu aracı kullanamazsınız.  
  
 Derlemelere [güçlü adlar](../../standard/assembly/strong-named.md) atabilmek genellikle yararlıdır veya gereklidir. Bu nedenle, Tlbimp.exe tanımlayıcı adlarla adlandırılmış derlemeler oluşturmak için gereken bilgileri sağlayan seçenekler içerir. Hem **/keyfile:** hem **de /keycontainer:** seçenekler güçlü adlara sahip derlemeleri imzalar. Bu nedenle, aynı anda bu seçeneklerden yalnızca birini sağlamak mantıklı olur.  
  
 **/başvuru** seçeneğini birden çok kez kullanarak birden çok başvuru derlemesi belirtebilirsiniz.

 Tlbimp.exe'nin derlemeler oluşturma şekli nedeniyle, bir derlemeyi farklı `mscorlib` bir sürüme yeniden hedeflemek mümkün değildir. Örneğin, .NET Framework 2.0'ı hedefleyen bir derleme oluşturmak istiyorsanız, .NET Framework 2.0/3.0/3.5 SDK ile gönderilen Tlbimp.exe kullanılmalıdır. .NET Framework 4.x'i hedeflemek için .NET Framework 4.x SDK ile gönderilen Tlbimp.exe kullanılmalıdır.

 Birden fazla tür kitaplığı içeren bir modülden bir tür kitaplığını içeri aktarırken, isteğe bağlı olarak tür kitaplık dosyasına bir kaynak kimliği eklenebilir. Tlbimp.exe bu dosyayı yalnızca geçerli dizinde ise ya da tam yolunu belirtirseniz bulabilir. Bu konunun ilerleyen kısımlarındaki örneğe bakın.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, .dll uzantılı `myTest.tlb` tür kitaplığıyla aynı ada sahip bir derleme oluşturur.  
  
```console  
tlbimp myTest.tlb
```  
  
 Aşağıdaki komut, adı `myTest.dll`ile bir derleme oluşturur.  
  
```console  
tlbimp  myTest.tlb  /out:myTest.dll  
```  
  
 Aşağıdaki komut, .dll uzantısı tarafından `MyModule.dll\1` belirtilen tür kitaplığıyla aynı ada sahip bir derleme oluşturur. `MyModule.dll\1`geçerli dizinde yer almalıdır.  
  
```console  
tlbimp MyModule.dll\1  
```  
  
 Aşağıdaki komut, tür kitaplığı `myTestLib.dll` `TestLib.dll`için adı olan bir derleme oluşturur. **/transform:dispret** seçeneği, tür kitaplığındaki dispinterfaces yöntemlerinin [out, retval] parametrelerini yönetilen kitaplıktaki iade değerlerine dönüştürür.  
  
```console  
tlbimp TestLib.dll /transform:dispret /out:myTestLib.dll  
```  
  
 Önceki örnekte tür kitaplığı, `TestLib.dll`geçersiz döndürür ve `SomeMethod` bir [out, retval] parametresi olan adlı bir dispinterface yöntemi içerir. Aşağıdaki kod giriş türü kitaplık yöntemi `SomeMethod` `TestLib.dll`imzası için .  
  
```cpp  
void SomeMethod([out, retval] VARIANT_BOOL*);  
```  
  
 **/transform:dispret** seçeneğini belirtmek Tlbimp.exe'nin `[out, retval]` `SomeMethod` parametresini `bool` bir geri dönüş değerine dönüştürmesine neden olur. Aşağıda Tlbimp.exe'nin **/transform:dispret** `myTestLib.dll` seçeneği belirtildiğinde yönetilen `SomeMethod` kitaplıkta ürettiği yöntem imzası verem.  
  
```csharp  
bool SomeMethod();  
```  
  
 **/transform:dispret**belirtmeden yönetilen bir `TestLib.dll` kitaplık oluşturmak için `SomeMethod` Tlbimp.exe kullanıyorsanız, araç yönetilen kitaplıkta `myTestLib.dll`aşağıdaki yöntem imzasını üretir.  
  
```csharp  
void SomeMethod(out bool x);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)](tlbexp-exe-type-library-exporter.md)
- [Tür Kitaplığını Derleme Olarak İçeri Aktarma](../interop/importing-a-type-library-as-an-assembly.md)
- [Tür Kitaplığı ndan Montaja Dönüşüm Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Ildasm.exe (IL Ayrıştırıcı)](ildasm-exe-il-disassembler.md)
- [Sn.exe (Tanımlayıcı Ad Aracı)](sn-exe-strong-name-tool.md)
- [Tanımlayıcı Adlı Derlemeler](../../standard/assembly/strong-named.md)
- [Tür Kitaplıklarını Interop Derlemelerine Alma Nitelikleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/y6a7ak23(v=vs.100))
- [Komut İstemleri](developer-command-prompt-for-vs.md)
