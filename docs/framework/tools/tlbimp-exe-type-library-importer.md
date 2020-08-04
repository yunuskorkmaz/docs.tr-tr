---
title: Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)
description: Tür kitaplığı Içeri aktarıcı Tlbimp.exe kullanın. Bu araç, bir COM tür kitaplığı içinde bulunan tür tanımlarını bir CLR derlemesinde eşdeğer tanımlara dönüştürür.
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
ms.openlocfilehash: f1e50336e6c159ae56b393098868e4b8f5310b49
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517002"
---
# <a name="tlbimpexe-type-library-importer"></a>Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)
Tür Kitaplığı İçeri Aktarma programı, COM tür kitaplığı içinde bulunan tür tanımlarını bir ortak dil çalışma zamanı derlemesi içindeki eşdeğer tanımlara dönüştürür. Tlbimp.exe'nin çıktısı, özgün tür kitaplığı içinde tanımlanan türler için çalışma zamanı meta verileri içeren bir ikili dosyadır (derleme). Bu dosyayı, [Ildasm.exe](ildasm-exe-il-disassembler.md)gibi araçlarla inceleyebilirsiniz.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
tlbimp tlbFile [options]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*Tlbdosya*|COM tür kitaplığı içeren herhangi bir dosyanın adı.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/asmversion:** *SürümNumarası*|Üretilecek derlemenin sürüm numarasını belirtir. *VersionNumber* ' i *ana. Minor. Build. Revision*biçiminde belirtin.|  
|**/Company:**`companyinformation`|Şirket bilgilerini çıktı derlemesine ekler.|  
|**/telif hakkı:**`copyrightinformation`|Çıktı derlemesine telif hakkı bilgileri ekler. Bu bilgiler, derleme için **dosya özellikleri** iletişim kutusunda görüntülenebilir.|  
|**/delaysign**|Elde edilen ve tanımlayıcı bir ada sahip olan derlemeyi gecikmeli imzalama yöntemiyle imzalamak için kullanılacak Tlbimp.exe'yi belirtir. Bu seçeneği **/keycontainer:**, **/keyfile:**, ya da **/publickey:** seçeneğiyle belirtmeniz gerekir. Gecikmeli imzalama işlemi hakkında daha fazla bilgi için bkz. [bir derlemeyi IMZALAMAYı geciktirme](../../standard/assembly/delay-sign.md).|  
|**/Help**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/keycontainer:** *ContainerName*|Sonuç bütünleştirilmiş kodu, *ContainerName*tarafından belirtilen anahtar kapsayıcısında bulunan ortak/özel anahtar çiftini kullanarak tanımlayıcı bir adla imzalar.|  
|**/keyfile:** *filename*|Sonuçta ortaya çıkan derlemeyi, yayımcının *dosya adında*bulunan resmi ortak/özel anahtar çiftini kullanarak tanımlayıcı bir adla imzalar.|  
|**/MACHINE:**`machinetype`|Belirtilen makine türünü (mikro işlemci) hedefleyen bir derleme oluşturur. Desteklenen makine türleri: x86, x64, Itanium ve Belirsiz.|  
|**/Namespace:** *ad alanı*|Derlemenin oluşturulacağı ad alanını belirtir.|  
|**/NoClassMembers**|Tlbimp.exe'nin sınıflara üye eklemesini önler. Bu, olası bir olasılık olduğunu önler <xref:System.TypeLoadException> .|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/Out:** *filename*|İçine meta veri tanımlarının yazılacağı çıktı dosyasının, derlemenin ve ad alanının adını belirtir. Tür kitaplığı, derlemenin ad alanını açıkça denetleyen arabirim tanım dili (IDL) özel özniteliğini belirtiyorsa **/Out** seçeneğinin derlemenin ad alanı üzerinde hiçbir etkisi yoktur. Bu seçeneği belirtmezseniz, Tlbimp.exe, girdi dosyasında tanımlanan asıl tür kitaplığıyla aynı ada sahip bir dosyaya meta verileri yazar ve ona bir .dll uzantısı atar. Çıktı dosyasının adı girdi dosyasının adıyla aynı ise, araç tür kitaplığı üzerine yazılmasını engellemek için bir hata üretir.|  
|**/birincil**|Belirtilen tür kitaplığı için bir birincil birlikte çalışma derlemesi oluşturur. Derlemeyi tür kitaplığı yayıncısının oluşturduğunu belirten bilgiler derlemeye eklenir. Birincil birlikte çalışma derlemesi belirterek, bir yayıncının derlemesini, Tlbimp.exe kullanarak tür kitaplığından oluşturulan diğer derlemelerden ayırt edersiniz. Yalnızca Tlbimp.exe ile içeri aktardığınız tür kitaplığının yayımcısıdır **/Primary** seçeneğini kullanmanız gerekir. Bir birincil birlikte çalışma derlemesini [tanımlayıcı bir adla](../../standard/assembly/strong-named.md)imzalamanız gerektiğini unutmayın. Daha fazla bilgi için bkz. [birincil birlikte çalışma derlemeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).|  
|**/Ürün:**`productinformation`|Çıktı derlemesine ürün bilgileri ekler. Bu bilgiler, derleme için **dosya özellikleri** iletişim kutusunda görüntülenebilir.|  
|**/ProductVersion:**`productversioninformation`|Çıktı derlemesine ürün sürümü ile ilgili bilgiler ekler. Biçim kısıtlamaları yoktur. Bu bilgiler, derleme için **dosya özellikleri** iletişim kutusunda görüntülenebilir.|  
|**/publickey:** *dosya adı*|Elde edilen derlemeyi imzalamak için kullanılacak ortak anahtarı içeren dosyayı belirtir. /PublicKey: ' nin yerine **/keyfile** : veya **/keycontainer** : seçeneğini **/publickey:** belirtirseniz Tlbimp.exe, **/keyfile:** veya **/keycontainer:** ile sağlanan ortak/özel anahtar çiftinden ortak anahtar oluşturur. **/Publickey:** seçeneği test anahtarını ve Gecikmeli imzalama senaryolarını destekler. Dosya, Sn.exe tarafından üretilen biçimdedir. Daha fazla bilgi için, tanımlayıcı ad aracında Sn.exe **-p** seçeneğine bakın [(Sn.exe)](sn-exe-strong-name-tool.md).|  
|**/Reference:** *dosya adı*|Geçerli tür kitaplığı dışında tanımlanmış tür başvurularını çözümlemek için kullanılacak derleme dosyasını belirtir. **/Reference** seçeneğini belirtmezseniz, Tlbimp.exe otomatik olarak tür kitaplığı içeri aktarılan tüm dış tür kitaplığını içeri aktarır. **/Reference** seçeneğini belirtirseniz, araç diğer tür kitaplıklarını içeri aktarmadan önce başvurulan derlemelerdeki dış türleri çözümlemeye çalışır.|  
|**/sessizlik:**`warningnumber`|Belirtilen uyarının görüntülenmesini bastırır. Bu seçenek **/Silent**ile kullanılamaz.|  
|**/silent**|Başarı iletilerinin görüntülenmesini bastırır. Bu seçenek **/sessizlik**ile kullanılamaz.|  
|**/strictref**|Araç geçerli derleme içindeki tüm başvuruları, **/Reference** seçeneğiyle belirtilen derlemeleri veya kayıtlı birincil birlikte çalışma derlemelerini (PIA 'lar) çözümleyemezse, bir tür kitaplığını içeri aktarmaz.|  
|**/strictref: nopıa**|**/Strictref**ile aynıdır, ancak PIA 'leri yoksayar.|  
|**/sysarray**|Bir COM stili SafeArray 'i yönetilen bir tür olarak içeri aktarmak için araca belirtir <xref:System.Array> .|  
|**/tlbreference:** *dosya adı*|Kayıt defterine danışmadan tür kitaplığı başvurularını çözümlemek için kullanılacak tür kitaplığı dosyasını belirtir.<br /><br /> Bu seçeneğin bazı eski tür kitaplığı biçimlerini yüklenmediğini unutmayın.  Ancak, kayıt defteri veya geçerli dizin aracılığıyla, eski tür kitaplığı biçimlerini dolaylı olarak yine yükleyebilirsiniz.|  
|**/ticari marka:**`trademarkinformation`|Çıktı derlemesine ticari marka bilgileri ekler. Bu bilgiler, derleme için **dosya özellikleri** iletişim kutusunda görüntülenebilir.|  
|**/Transform:** *transformname*|*Transformname* parametresi tarafından belirtilen meta verileri dönüştürür.<br /><br /> Yalnızca dağıtım arabirimlerinde (dispınterfaces) yöntemlerin [Out, retval] parametrelerini dönüş değerlerine dönüştürmek için *transformname* parametresinin **dispret** değerini belirtin.<br /><br /> Bu seçenek hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerindeki örneklere bakın.|  
|**/unsafe**|Arabirimleri, .NET Framework güvenlik denetimleri olmadan üretir. Bu şekilde sunulan bir yöntemi çağırmak güvenlik riski oluşturabilir. Bu tür kodları ortaya çıkarmanın getireceği riskleri bilmiyorsanız bu seçeneği kullanmamalısınız.|  
|**/verbose**|Ayrıntılı modu belirtir; içeri aktarılan tür kitaplığı hakkında daha fazla bilgi görüntüler.|  
|**/VariantBoolFieldToBool**|`VARIANT_BOOL`Yapılardaki alanları öğesine dönüştürür <xref:System.Boolean> .|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
> [!NOTE]
> Tlbimp.exe için komut satırı seçenekleri büyük/küçük harfe duyarlı değildir ve herhangi bir sırayla sağlanabilir. Tek yapmanız gereken, onu benzersiz şekilde tanımlamak için seçeneği yeterince belirtmektir. Bu nedenle, **/n** **/nologo** ve **/ou** ile eşdeğerdir: *outfile.dll* **/Out:** *outfile.dll*ile eşdeğerdir.  
  
## <a name="remarks"></a>Açıklamalar  
 Tlbimp.exe dönüştürmeleri tüm tür Kitaplığında bir defada gerçekleştirir. Tek bir tür kitaplığı içinde tanımlanmış bir tür alt kümesi için tür bilgileri oluştururken bu aracı kullanamazsınız.  
  
 Derlemelere [tanımlayıcı adlar](../../standard/assembly/strong-named.md) atayabilmesi genellikle yararlı veya gereklidir. Bu nedenle, Tlbimp.exe tanımlayıcı adlarla adlandırılmış derlemeler oluşturmak için gereken bilgileri sağlayan seçenekler içerir. Hem **/keyfile:** hem de **/keycontainer:** seçenekler derlemeleri tanımlayıcı adlarla imzalar. Bu nedenle, aynı anda bu seçeneklerden yalnızca birini sağlamak mantıklı olur.  
  
 **/Reference** seçeneğini birden çok kez kullanarak birden çok başvuru derlemesi belirleyebilirsiniz.

 Tlbimp.exe derlemeleri oluşturma yöntemi nedeniyle, bir derlemeyi farklı bir sürüme yeniden hedeflemeniz mümkün değildir `mscorlib` . Örneğin, .NET Framework 2,0 ' i hedefleyen bir derleme oluşturmak isterseniz, .NET Framework 2.0/3.0/3.5 SDK ile gönderilen Tlbimp.exe kullanılmalıdır. .NET Framework 4. x ' i hedeflemek için, bir .NET Framework 4. x SDK ile gönderilen Tlbimp.exe kullanılmalıdır.

 Birden fazla tür kitaplığı içeren bir modülden bir tür kitaplığını içeri aktarırken, isteğe bağlı olarak tür kitaplık dosyasına bir kaynak kimliği eklenebilir. Tlbimp.exe bu dosyayı yalnızca geçerli dizinde ise ya da tam yolunu belirtirseniz bulabilir. Bu konunun ilerleyen kısımlarındaki örneğe bakın.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, `myTest.tlb` . dll uzantısıyla ve ' de bulunan tür kitaplığıyla aynı ada sahip bir derleme oluşturur.  
  
```console  
tlbimp myTest.tlb
```  
  
 Aşağıdaki komut, adında bir derleme oluşturur `myTest.dll` .  
  
```console  
tlbimp  myTest.tlb  /out:myTest.dll  
```  
  
 Aşağıdaki komut, `MyModule.dll\1` . dll uzantısıyla ve tarafından belirtilen tür kitaplığıyla aynı ada sahip bir derleme oluşturur. `MyModule.dll\1`geçerli dizinde bulunmalıdır.  
  
```console  
tlbimp MyModule.dll\1  
```  
  
 Aşağıdaki komut, tür kitaplığının adına sahip bir derleme oluşturur `myTestLib.dll` `TestLib.dll` . **/Transform: dispret** seçeneği, tür kitaplığındaki dispınterfaces üzerinde bulunan tüm [Out, retval] parametrelerini yönetilen kitaplıktaki dönüş değerlerine dönüştürür.  
  
```console  
tlbimp TestLib.dll /transform:dispret /out:myTestLib.dll  
```  
  
 Yukarıdaki örnekteki tür kitaplığı, `TestLib.dll` `SomeMethod` void döndüren ve bir [Out, retval] parametresine sahip adlı bir dispınterface yöntemi içerir. Aşağıdaki kod, içindeki için giriş türü kitaplığı Yöntem imzasıdır `SomeMethod` `TestLib.dll` .  
  
```cpp  
void SomeMethod([out, retval] VARIANT_BOOL*);  
```  
  
 **/Transform: dispret** seçeneğinin belirtilmesi Tlbimp.exe `[out, retval]` parametresini `SomeMethod` bir dönüş değerine dönüştürmesine neden olur `bool` . Aşağıda, `SomeMethod` `myTestLib.dll` **/Transform: dispret** seçeneği belirtildiğinde yönetilen kitaplıkta için Tlbimp.exe ürettiği Yöntem imzası verilmiştir.  
  
```csharp  
bool SomeMethod();  
```  
  
 `TestLib.dll` **/Transform: dispret**belirtmeden bir yönetilen kitaplık oluşturmak için Tlbimp.exe kullanıyorsanız, araç yönetilen kitaplıkta için aşağıdaki yöntem imzasını üretir `SomeMethod` `myTestLib.dll` .  
  
```csharp  
void SomeMethod(out bool x);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Tlbexp.exe (tür kitaplığı verme programı)](tlbexp-exe-type-library-exporter.md)
- [Tür Kitaplığını Derleme Olarak İçeri Aktarma](../interop/importing-a-type-library-as-an-assembly.md)
- [Tür kitaplığını derlemeye dönüştürme Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Ildasm.exe (Il ayırıcı)](ildasm-exe-il-disassembler.md)
- [Sn.exe (tanımlayıcı ad aracı)](sn-exe-strong-name-tool.md)
- [Tanımlayıcı adlı derlemeler](../../standard/assembly/strong-named.md)
- [Tür kitaplıklarını birlikte çalışma derlemelerine Içeri aktarmaya yönelik öznitelikler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/y6a7ak23(v=vs.100))
- [Komut Istemleri](developer-command-prompt-for-vs.md)
