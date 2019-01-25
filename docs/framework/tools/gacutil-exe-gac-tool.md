---
title: Gacutil.exe (Genel Derleme Önbelleği Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- global assembly cache, manipulating contents
- GAC (global assembly cache), Gacutil.exe
- Gacutil.exe
- GAC (global assembly cache), viewing contents
- installing assemblies into global assembly cache
- removing assemblies from global assembly cache
- list of assemblies in global assembly cache
- cache [.NET Framework], global assembly cache
- GAC (global assembly cache), manipulating contents
- global assembly cache, Gacutil.exe
- Global Assembly Cache tool
ms.assetid: 4c7be9c8-72ae-481f-a01c-1a4716806e99
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 779cf36fb10cc3acbefabd6ef90a885cc221f3f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541228"
---
# <a name="gacutilexe-global-assembly-cache-tool"></a>Gacutil.exe (Genel Derleme Önbelleği Aracı)
Genel Bütünleştirilmiş Kod Önbelleği aracı genel bütünleştirilmiş kod önbelleğinin ve indirme önbelleğinin içeriğini görüntülemenize ve değiştirmenize olanak sağlar.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici Komut İstemi'ni kullanın. Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
gacutil [options] [assemblyName | assemblyPath | assemblyListFile]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*AssemblyName*|Bir derlemenin adı. Gibi bir kısmen belirtilen derleme adı sağlayabilirsiniz `myAssembly` veya tam olarak belirtilen derleme adı gibi `myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5`.|  
|*assemblyPath*|Bir derleme bildirimi içeren dosyanın adı.|  
|*assemblyListFile*|Yüklenecek veya kaldırılacak derlemeleri listeleyen bir ANSI metin dosyasının yolu. Derlemeleri yüklemek üzere metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda yolu belirtin. Araç göreli yolları konumunu yorumlama *assemblyListFile*. Derlemeleri kaldırmak üzere bir metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda tam derleme adını belirtin. Bkz: *assemblyListFile* içeriği daha sonra bu konudaki örnekler.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/CDL**|İndirme önbelleğinin içeriğini siler.|  
|**/f**|Bu seçeneği belirtin **/i** veya **/il** bir derlemeyi yeniden yüklemeye zorlamak için Seçenekler. Eğer genel bütünleştirilmiş kod önbelleğinde aynı ada sahip bir derleme zaten bulunuyorsa, araç onun üzerine yazar.|  
|**/h**[**elp**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/i** *assemblyPath*|Genel bütünleştirilmiş kod önbelleğine bir derleme yükler.|  
|**/if** *assemblyPath*|Genel bütünleştirilmiş kod önbelleğine bir derleme yükler. Eğer genel bütünleştirilmiş kod önbelleğinde aynı ada sahip bir derleme zaten bulunuyorsa, araç onun üzerine yazar.<br /><br /> Bu seçeneği belirtmek belirtmeye eşdeğerdir **/i** ve **/f** seçeneklerini birlikte.|  
|**/İl** *assemblyListFile*|Belirtilen bir veya daha fazla bütünleştirilmiş kodları yükler *assemblyListFile* genel bütünleştirilmiş kod önbelleğine.|  
|**Description** *assemblyPath*<br /><br /> *Düzeni*<br /><br /> *id*<br /><br /> *Açıklaması*|Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler ve derlemeyi saymak için bir başvuru ekler. Belirtmelisiniz *assemblyPath*, *düzeni*, *kimliği*, ve *açıklama* bu seçenekle parametreleri. Bu parametreler için belirtebileceğiniz geçerli değerlerin bir açıklaması için bkz: **/r** seçeneği.<br /><br /> Bu seçeneği belirtmek belirtmeye eşdeğerdir **/i** ve **/r** seçeneklerini birlikte.|  
|**/l** [*assemblyName*]|Genel bütünleştirilmiş kod önbelleğinin içeriğini listeler. Belirtirseniz *assemblyName* parametre, araç yalnızca o adla eşleşen derlemeleri listeler.|  
|**/ldl**|İndirilen dosyalar önbelleğinin içeriğini listeler.|  
|**/lr** [*assemblyName*]|Tüm derlemeleri ve karşılık gelen başvuru sayılarını listeler. Belirtirseniz *assemblyName* parametresi, araç yalnızca o adla eşleşen derlemeleri listeler ve bunların karşılık gelen başvuru sayılarını.|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/r** [*assemblyName &#124; assemblyPath*]<br /><br /> *Düzeni*<br /><br /> *id*<br /><br /> *Açıklaması*|Yüklenecek veya kaldırılacak bir derleme veya derlemeler için izlenen bir başvuru belirtir. Bu seçeneği belirtin **/i**, **/il**, **/u**, veya **/ul** seçenekleri.<br /><br /> Bir derlemeyi yüklemek için bu seçeneği belirtin *assemblyPath*, *düzeni*, *kimliği*, ve *açıklama* bu seçenekle parametreleri. Bir derlemeyi kaldırmak için bu seçeneği belirtin *assemblyName*, *düzeni*, *kimliği*, ve *açıklama* parametreleri.<br /><br /> Bir derlemeye olan başvuruyu kaldırmak için aynı belirtmelisiniz *düzeni*, *kimliği*, ve *açıklama* belirtilen parametreleri **/i** ve **/r** (veya **Description**) derleme yüklenirken seçenekleri. Eğer bir derlemeyi kaldırıyorsanız, eğer kaldırılacak son başvuruysa ve Windows Installer'ın o derlemeye hiçbir başvurusu yok ise araç derlemeyi genel bütünleştirilmiş kod önbelleğinden de kaldırır.<br /><br /> *Düzeni* parametresi yükleme düzeninin türünü belirtir. Aşağıdaki değerlerden birini belirleyebilirsiniz.<br /><br /> -UNINSTALL_KEY: Microsoft Windows Yükleyici uygulamayı Program Ekle/Kaldır eklerse, bu değeri belirtin. Uygulamalar HKLM\Software\Microsoft\Windows\CurrentVersion içine bir kayıt defteri anahtarı ekleyerek kendilerini Program Ekle/Kaldır'a ekler.<br />-DOSYA YOLU: Yükleyici uygulamayı Program Ekle/Kaldır'a eklemiyorsa bu değeri belirtin.<br />-DONUK: Bir kayıt defteri anahtarı varsa, bu değeri belirtin veya dosya yolu sağlamak yükleme senaryonuz için geçerli değildir. Bu değer için özel bilgi belirtmenize olanak tanır *kimliği* parametresi.<br /><br /> İçin belirtilecek değeri *kimliği* parametresi için belirtilen değere bağlıdır *düzeni* parametresi:<br /><br /> -İçin unınstall_key belirtirseniz, *düzeni* parametresi, HKLM\Software\Microsoft\Windows\CurrentVersion kayıt defteri anahtarında ayarlanan uygulama adını belirtin. Örneğin, kayıt defteri anahtarı HKLM\Software\Microsoft\Windows\CurrentVersion\MyApp ise için MyApp belirtin. *kimliği* parametresi.<br />-İçin FILEPATH belirtirseniz, *düzeni* parametresi olarak derlemeyi yükleyen yürütülebilir dosyanın tam yolunu belirtmeniz *kimliği* parametresi.<br />-İçin OPAQUE belirtirseniz, *düzeni* parametre, verilerin herhangi bir bilgiyi sağlayabilirler *kimliği* parametresi. Belirttiğiniz veri tırnak işaretleri ("") arasına alınmalıdır.<br /><br /> *Açıklama* parametresi yüklenecek uygulama hakkında açıklayıcı metin belirlemenize olanak verir. Bu bilgi başvurular numaralandığında görüntülenir.|  
|**/silent**|Tüm çıktıların görüntülenmesini bastırır.|  
|**/u** *assemblyName*|Genel bütünleştirilmiş kod önbelleğinden bir derlemeyi kaldırır.|  
|**/UF** *assemblyName*|Belirtilen bir derlemenin tüm başvurularını kaldırarak derlemeyi kaldırmaya zorlar.<br /><br /> Bu seçeneği belirtmek belirtmeye eşdeğerdir **/u** ve **/f** seçeneklerini birlikte. **Not:**  Bu seçeneği, Microsoft Windows Installer kullanarak yüklenen bir derlemeyi kaldırmak için kullanamazsınız. Eğer bu işlemi yapmayı denerseniz, araç bir hata iletisi görüntüler.|  
|**/UL** *assemblyListFile*|Belirtilen bir veya daha fazla derlemeleri kaldırır *assemblyListFile* genel bütünleştirilmiş kod önbelleğinden.|  
|**/u**[**ngen**] *assemblyName*|Belirtilen bir derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırır. Eğer belirtilen derlemenin varolan başvuru sayısı varsa, araç başvuru sayılarını görüntüler ve derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırmaz. **Not:**  .NET Framework sürüm 2.0 `/ungen` desteklenmiyor. Bunun yerine, `uninstall` komutu [Ngen.exe (yerel Görüntü Oluşturucu)](../../../docs/framework/tools/ngen-exe-native-image-generator.md). <br /><br /> .NET Framework sürümleri 1.0 ve 1.1 içinde belirtme **/ ungen** derlemeyi yerel görüntü önbelleğinden kaldırmak Gacutil.exe neden olur. Bu önbellek kullanılarak oluşturulan derlemeler için yerel görüntüleri depolar [Ngen.exe (yerel Görüntü Oluşturucu)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|  
|**/ur** *assemblyName*<br /><br /> *Düzeni*<br /><br /> *id*<br /><br /> *Açıklaması*|Belirtilen bir derleme için genel bütünleştirilmiş kod önbelleğinden bir başvuru kaldırır. Bir derlemeye olan başvuruyu kaldırmak için aynı belirtmelisiniz *düzeni*, *kimliği*, ve *açıklama* belirtilen parametreleri **/i** ve **/r** (veya **Description)** derleme yüklenirken seçenekleri. Bu parametreler için belirtebileceğiniz geçerli değerlerin bir açıklaması için bkz: **/r** seçeneği.<br /><br /> Bu seçeneği belirtmek belirtmeye eşdeğerdir **/u** ve **/r** seçeneklerini birlikte.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Gacutil.exe'yi kullanabilmek için yönetici ayrıcalıklarınız olmalıdır.  
  
 Özellikle, Gacutil.exe önbelleğe derlemeler yüklemenize, önbellekten derlemeleri kaldırmanıza ve önbelleğin içeriğini listelemenize olanak sağlar.  
  
 Gacutil.exe, Windows Installer tarafından desteklenen başvuru sayma düzenine benzer başvuru saymayı destekleyen seçenekler sağlar. Gacutil.exe'yi kullanarak aynı derlemeyi yükleyen iyi uygulamayı yükleyebilirsiniz: araç o derlemeye olan başvuruların sayısını takip eder. Sonuç olarak, derleme iki uygulama da kaldırılana kadar bilgisayarda kalır. Eğer Gacutil.exe'yi gerçek ürün yüklemelerinde kullanıyorsanız, başvuru saymayı destekleyen seçenekleri kullanın. Kullanım **/i** ve **/r** birlikte bir derlemeyi yüklemek ve ona bir başvuru sayısı eklemek için Seçenekler. Kullanım **/u** ve **/r** birlikte bir derleme için bir başvuru sayısını kaldırmak için seçenekleri. Unutmayın, kullanarak **/i** ve **/u** seçeneklerini tek başına başvuru sayımı desteklemez. Bu seçenekler uygulama geliştirme süresince kullanılmaya uygundur ancak gerçek ürün yüklemelerinde uygun değildir.  
  
 Kullanım **/il** veya **/ul** yüklemek veya bir ANSI metin dosyasında tutulan derleme listesini kaldırmak için seçenekleri. Metin dosyasının içeriği doğru şekilde biçimlendirilmelidir. Derlemeleri yüklemek üzere metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda yolu belirtin. Aşağıdaki örnek yüklenecek derlemeleri içeren bir dosyanın içeriğini gösterir.  
  
```  
myAssembly1.dll  
myAssembly2.dll  
myAssembly3.dll  
```  
  
 Derlemeleri kaldırmak üzere bir metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda tam derleme adını belirtin. Aşağıdaki örnek kaldırılacak derlemeleri içeren bir dosyanın içeriğini gösterir.  
  
```  
myAssembly1,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab  
myAssembly2,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab  
myAssembly3,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab  
```  

> [!NOTE]
>  (Dosya uzantısı hariç) 79 ve 91 karakter arasında daha uzun bir dosya adına sahip bir derlemeyi yüklenmeye çalışılırken şu hataya neden olabilir:
> ```
> Failure adding assembly to the cache:   The file name is too long.
> ```
> Bu durum, dahili olarak, aşağıdaki öğeleri içeren bir yol MAX_PATH karaktere kadar Gacutil.exe oluşturur çünkü:
> - GAC Root - 34 karakter (örn. `C:\Windows\Microsoft.NET\assembly\`)
> - (Örn. mimarisi - 7 veya 9 karakter `GAC_32\`, `GAC_64\`, `GAC_MSIL`)
> - AssemblyName - 91 karakter, diğer öğeleri (örn boyutuna bağlı olarak en fazla. `System.Xml.Linq\`)
> - AssemblyInfo - 31 için 48 karakter veya daha fazla oluşan:
>   - Framework - 5 (örn. karakter `v4.0_`)
>   - AssemblyVersion - 8-24 karakter (örn.) `9.0.1000.0_`)
>   - AssemblyLanguage - 1-8 karakter (örn.) `de_`, `sr-Cyrl_`)
>   - PublicKey - 17 karakter (örn.) `31bf3856ad364e35\`)
> - DllFileName - kadar 91 + 4 karakter (örn. `<AssemblyName>.dll`)

## <a name="examples"></a>Örnekler  
 Aşağıdaki komutu yükler `mydll.dll` genel bütünleştirilmiş kod önbelleğine.  
  
```  
gacutil /i mydll.dll  
```  
  
 Aşağıdaki komut, derlemeyi kaldırır `hello` genel bütünleştirilmiş kod önbelleği başvuru sayısı bulunmadığı sürece mevcut derleme için.  
  
```  
gacutil /u hello  
```  
  
 Önceki komutun, derleme adı tam olarak belirtilmediği için derleme önbelleğinden birden fazla derleme kaldırabileceğine dikkat edin. Örneğin, her iki sürüm 1.0.0.0 ve 3.2.2.1 `hello` komutu önbelleğinde yüklü `gacutil /u hello` de kaldırır.  
  
 Birden fazla derlemeyi kaldırmayı önlemek için aşağıdaki örneği kullanın. Bu komut yalnızca kaldırır `hello` tam sürüm numarasını, kültür ve ortak anahtarı eşleşen derleme.  
  
```  
gacutil /u hello, Version=1.0.0.1, Culture="de",PublicKeyToken=45e343aae32233ca  
```  
  
 Aşağıdaki komut dosyasında belirtilen derlemeleri yükler `assemblyList.txt` genel bütünleştirilmiş kod önbelleğine.  
  
 `gacutil /il assemblyList.txt`  
  
 Aşağıdaki komut dosyasında belirtilen derlemeleri kaldırır `assemblyList.txt` genel bütünleştirilmiş kod önbelleğinden.  
  
 `gacutil /ul assemblyList.txt`  
  
 Aşağıdaki komut yükler `myDll.dll` genel bütünleştirilmiş kod önbelleğine ve ona bir başvuru sayısı ekler. Derleme `myDll.dll` uygulama tarafından kullanılan `MyApp`. `UNINSTALL_KEY MyApp` Parametresinin belirttiği eklediği kayıt defteri anahtarı `MyApp` için Windows içinde Program Ekle/Kaldır. Açıklama parametresi olarak belirtilen `My Application Description`.  
  
```  
gacutil /i /r myDll.dll UNINSTALL_KEY MyApp "My Application Description"  
```  
  
 Aşağıdaki komut yükler `myDll.dll` genel bütünleştirilmiş kod önbelleğine ve ona bir başvuru sayısı ekler. Düzen parametresi `FILEPATH`ve ID parametresi `c:\applications\myApp\myApp.exe`, yüklenen uygulama yolunu belirtin `myDll.dll.` açıklama parametresi olarak belirtilen `MyApp`.  
  
 `gacutil /i /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp`  
  
 Aşağıdaki komut yükler `myDll.dll` genel bütünleştirilmiş kod önbelleğine ve ona bir başvuru sayısı ekler. Düzen parametresi `OPAQUE`, kimlik ve açıklama parametrelerini özelleştirmenize olanak sağlar.  
  
```  
gacutil /i /r mydll.dll OPAQUE "Insert custom application details here" "Insert Custom description information here"  
```  
  
 Aşağıdaki komut başvurusunu kaldırır `myDll.dll` uygulama tarafından `myApp`. Eğer bu, derleme için olan son başvuruysa, derlemeyi ayrıca genel bütünleştirilmiş kod önbelleğinden de kaldırır.  
  
 `gacutil /u /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp`  
  
 Aşağıdaki komut genel bütünleştirilmiş kod önbelleğinin içeriğini listeler.  
  
```  
gacutil /l  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Araçlar](../../../docs/framework/tools/index.md)
- [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)
- [Regasm.exe (Derleme Kayıt Aracı)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)
- [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
