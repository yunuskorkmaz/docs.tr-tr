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
ms.openlocfilehash: 87f3cb799ba4e406906759e1facd19d00c8bdace
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73107497"
---
# <a name="gacutilexe-global-assembly-cache-tool"></a>Gacutil.exe (Genel Derleme Önbelleği Aracı)

Genel Bütünleştirilmiş Kod Önbelleği aracı genel bütünleştirilmiş kod önbelleğinin ve indirme önbelleğinin içeriğini görüntülemenize ve değiştirmenize olanak sağlar.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
gacutil [options] [assemblyName | assemblyPath | assemblyListFile]
```

## <a name="parameters"></a>Parametreler

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|*Assemblyname*|Bir derlemenin adı. Kısmen belirtilmiş bir derleme adı `myAssembly` veya '. `myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5`|
|*Assemblypath*|Bir derleme bildirimi içeren dosyanın adı.|
|*assemblyListDosya*|Yüklenecek veya kaldırılacak derlemeleri listeleyen bir ANSI metin dosyasının yolu. Derlemeleri yüklemek üzere metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda yolu belirtin. Araç, *assemblyListFile'Nin*konumuna göre göreli yolları yorumlar. Derlemeleri kaldırmak üzere bir metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda tam derleme adını belirtin. Bu konuda daha sonra *assemblyListFile* içeriği örneklerine bakın.|

|Seçenek|Açıklama|
|------------|-----------------|
|**/cdl**|İndirme önbelleğinin içeriğini siler.|
|**/f**|Bir derlemeyi yeniden yüklemeye zorlamak için **/i** veya **/il** seçenekleriyle bu seçeneği belirtin. Eğer genel bütünleştirilmiş kod önbelleğinde aynı ada sahip bir derleme zaten bulunuyorsa, araç onun üzerine yazar.|
|**/h**[**elp**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|**/i** *assemblyPath*|Genel bütünleştirilmiş kod önbelleğine bir derleme yükler.|
|**/if**  *assemblyPath*|Genel bütünleştirilmiş kod önbelleğine bir derleme yükler. Eğer genel bütünleştirilmiş kod önbelleğinde aynı ada sahip bir derleme zaten bulunuyorsa, araç onun üzerine yazar.<br /><br /> Bu seçeneğin **belirtilmesi, /i** ve **/f** seçeneklerini birlikte belirtmeye eşdeğerdir.|
|**/il** *assemblyListFile*|*AssemblyListFile'da* belirtilen bir veya daha fazla derlemeyi genel derleme önbelleğine yükler.|
|**/ir**  *assemblyPath*<br /><br /> *düzen*<br /><br /> *Kimliği*<br /><br /> *Açıklama*|Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler ve derlemeyi saymak için bir başvuru ekler. Bu seçenekle *assemblyPath,* *düzeni,* *id*ve *açıklama* parametrelerini belirtmeniz gerekir. Bu parametreler için belirtebileceğiniz geçerli değerlerin açıklaması için **/r** seçeneğine bakın.<br /><br /> Bu seçeneğin **belirtilmesi, /i** ve **/r** seçeneklerini birlikte belirtmeye eşdeğerdir.|
|**/l** [*assemblyName*]|Genel bütünleştirilmiş kod önbelleğinin içeriğini listeler. *AssemblyName* parametresini belirtirseniz, araç yalnızca bu ada uyan derlemeleri listeler.|
|**/ldl**|İndirilen dosyalar önbelleğinin içeriğini listeler.|
|**/lr** [*assemblyName*]|Tüm derlemeleri ve karşılık gelen başvuru sayılarını listeler. *AssemblyName* parametresini belirtirseniz, araç yalnızca bu ada uyan derlemeleri ve bunların karşılık gelen başvuru sayılarını listeler.|
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|
|**/r** [*assemblyName &#124; assemblyPath*]<br /><br /> *düzen*<br /><br /> *Kimliği*<br /><br /> *Açıklama*|Yüklenecek veya kaldırılacak bir derleme veya derlemeler için izlenen bir başvuru belirtir. Bu seçeneği **/i**, **/il**, **/u**veya **/ul** seçenekleriyle belirtin.<br /><br /> Bir derleme yüklemek için, bu seçenekle *assemblyPath,* *düzen,* *id*ve açıklama parametrelerini *belirtin.* Bir derlemeyi kaldırmak için *assemblyName,* düzen, *id*ve açıklama parametrelerini *belirtin.* *description*<br /><br /> Bir derlemeye yapılan başvuruyu kaldırmak için, derleme yüklendiğinde **/i** ve **/r** (veya **/ir)** seçenekleriyle belirtilen aynı *şema,* *id*ve *açıklama* parametrelerini belirtmeniz gerekir. Eğer bir derlemeyi kaldırıyorsanız, eğer kaldırılacak son başvuruysa ve Windows Installer'ın o derlemeye hiçbir başvurusu yok ise araç derlemeyi genel bütünleştirilmiş kod önbelleğinden de kaldırır.<br /><br /> *Şema* parametresi yükleme düzeninin türünü belirtir. Aşağıdaki değerlerden birini belirleyebilirsiniz.<br /><br /> - UNINSTALL_KEY: Yükleyici uygulamayı Microsoft Windows'da Programlar Ekle/Kaldır'a ekliyorsa bu değeri belirtin. Uygulamalar HKLM\Software\Microsoft\Windows\CurrentVersion içine bir kayıt defteri anahtarı ekleyerek kendilerini Program Ekle/Kaldır'a ekler.<br />- FILEPATH: Yükleyici uygulamayı Programlar Ekle/Kaldır'a eklemiyorsa bu değeri belirtin.<br />- OPAK: Bir kayıt defteri anahtarı veya dosya yolu sağlama yükleme senaryonuz için geçerli değilse bu değeri belirtin. Bu değer, *kimlik* parametresi için özel bilgileri belirtmenizi sağlar.<br /><br /> *Id* parametresi için belirtilen değer, *şema* parametresi için belirtilen değere bağlıdır:<br /><br /> - *Şema* parametresi için UNINSTALL_KEY belirtirseniz, HKLM\Software\Microsoft\Windows\CurrentVersion kayıt defteri anahtarında ayarlanan uygulamanın adını belirtin. Örneğin, kayıt defteri anahtarı HKLM\Software\Microsoft\Windows\CurrentVersion\MyApp *ise, kimlik* parametresi için MyApp'ı belirtin.<br />- *Şema* parametresi için FILEPATH belirtirseniz, derlemeyi *kimlik* parametresi olarak yükleyen yürütülebilir dosyaya tam yolu belirtin.<br />- *Şema* parametresi için OPAK belirtirseniz, herhangi bir veri parçasını *kimlik* parametresi olarak sağlayabilirsiniz. Belirttiğiniz veri tırnak işaretleri ("") arasına alınmalıdır.<br /><br /> *Açıklama* parametresi, yüklenmesi gereken uygulama hakkında açıklayıcı metin belirtmenize olanak tanır. Bu bilgi başvurular numaralandığında görüntülenir.|
|**/silent**|Tüm çıktıların görüntülenmesini bastırır.|
|**/u**  *assemblyName*|Genel bütünleştirilmiş kod önbelleğinden bir derlemeyi kaldırır.|
|**/uf**  *assemblyName*|Belirtilen bir derlemenin tüm başvurularını kaldırarak derlemeyi kaldırmaya zorlar.<br /><br /> Bu seçeneğin **belirtilmesi, /u** ve **/f** seçeneklerini birlikte belirtmeye eşdeğerdir. **Not:**  Microsoft Windows Installer kullanılarak yüklenen bir derlemeyi kaldırmak için bu seçeneği kullanamazsınız. Eğer bu işlemi yapmayı denerseniz, araç bir hata iletisi görüntüler.|
|**/ul** *assemblyListFile*|*AssemblyListFile'da* belirtilen bir veya daha fazla derlemeyi genel derleme önbelleğinden kaldır.|
|**/u**[**ngen**] *assemblyName*|Belirtilen bir derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırır. Eğer belirtilen derlemenin varolan başvuru sayısı varsa, araç başvuru sayılarını görüntüler ve derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırmaz. **Not:**  .NET Framework sürüm 2.0'da `/ungen` desteklenmez. Bunun yerine, `uninstall` [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md)komutunu kullanın. <br /><br /> .NET Framework sürümleri 1.0 ve 1.1'de,/ungen belirtilmesi Gacutil.exe'nin derlemeyi yerel görüntü önbelleğinden kaldırmasına neden olur. **/ungen** Bu önbellek, [Ngen.exe (Yerel Görüntü Oluşturucusu)](ngen-exe-native-image-generator.md)kullanılarak oluşturulan derlemeler için yerel görüntüleri depolar.|
|**/ur**  *assemblyName*<br /><br /> *düzen*<br /><br /> *Kimliği*<br /><br /> *Açıklama*|Belirtilen bir derleme için genel bütünleştirilmiş kod önbelleğinden bir başvuru kaldırır. Bir derlemeye yapılan başvuruyu kaldırmak için, derleme yüklendiğinde **/i** ve **/r** (veya **/ir)** seçenekleriyle belirtilen aynı *şema,* *id*ve *açıklama* parametrelerini belirtmeniz gerekir. Bu parametreler için belirtebileceğiniz geçerli değerlerin açıklaması için **/r** seçeneğine bakın.<br /><br /> Bu seçeneğin **belirtilmesi, /u** ve **/r** seçeneklerini birlikte belirtmeye eşdeğerdir.|
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|

## <a name="remarks"></a>Açıklamalar

> [!NOTE]
> Gacutil.exe'yi kullanabilmek için yönetici ayrıcalıklarınız olmalıdır.

Özellikle, Gacutil.exe önbelleğe derlemeler yüklemenize, önbellekten derlemeleri kaldırmanıza ve önbelleğin içeriğini listelemenize olanak sağlar.

Gacutil.exe, Windows Installer tarafından desteklenen başvuru sayma düzenine benzer başvuru saymayı destekleyen seçenekler sağlar. Gacutil.exe'yi kullanarak aynı derlemeyi yükleyen iyi uygulamayı yükleyebilirsiniz: araç o derlemeye olan başvuruların sayısını takip eder. Sonuç olarak, derleme iki uygulama da kaldırılana kadar bilgisayarda kalır. Eğer Gacutil.exe'yi gerçek ürün yüklemelerinde kullanıyorsanız, başvuru saymayı destekleyen seçenekleri kullanın. Bir derleme yüklemek ve saymak için bir referans eklemek için **birlikte /i** ve **/r** seçeneklerini kullanın. Derleme için başvuru sayısını kaldırmak için **/u** ve **/r** seçeneklerini birlikte kullanın. **/i** ve **/u** seçeneklerini tek başına kullanmanın referans saymayı desteklemediğini unutmayın. Bu seçenekler uygulama geliştirme süresince kullanılmaya uygundur ancak gerçek ürün yüklemelerinde uygun değildir.

ANSI metin dosyasında depolanan derlemelerin listesini yüklemek veya kaldırmak için **/il** veya **/ul** seçeneklerini kullanın. Metin dosyasının içeriği doğru şekilde biçimlendirilmelidir. Derlemeleri yüklemek üzere metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda yolu belirtin. Aşağıdaki örnek yüklenecek derlemeleri içeren bir dosyanın içeriğini gösterir.

```text
myAssembly1.dll
myAssembly2.dll
myAssembly3.dll
```

Derlemeleri kaldırmak üzere bir metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda tam derleme adını belirtin. Aşağıdaki örnek kaldırılacak derlemeleri içeren bir dosyanın içeriğini gösterir.

```text
myAssembly1,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab
myAssembly2,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab
myAssembly3,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab
```

> [!NOTE]
> 79 ile 91 karakter arasında (dosya uzantısı hariç) daha uzun bir dosya adı ile bir derleme yüklemeye çalışmak aşağıdaki hataya neden olabilir:
>
> ```output
> Failure adding assembly to the cache:   The file name is too long.
> ```
>
> Bunun nedeni, dahili Gacutil.exe'nin aşağıdaki öğelerden oluşan en fazla MAX_PATH karakterden oluşan bir yol oluşturmasıdır:
>
> - GAC Kök - 34 chars (yani. `C:\Windows\Microsoft.NET\assembly\`)
> - Mimarlık - 7 veya 9 chars (yani. `GAC_32\`, `GAC_64\`, `GAC_MSIL`)
> - AssemblyName - Diğer öğelerin boyutuna bağlı olarak 91 karaktere kadar (örn. `System.Xml.Linq\`)
> - AssemblyInfo - 31 ila 48 chars veya daha fazla oluşan:
>   - Çerçeve - 5 chars (örneğin. `v4.0_`)
>   - AssemblyVersion - 8-24 chars (örneğin. `9.0.1000.0_`)
>   - AssemblyLanguage - 1-8 chars (örneğin. `de_`, `sr-Cyrl_`)
>   - PublicKey - 17 chars (örneğin. `31bf3856ad364e35\`)
> - DllFileName - 91 + 4 karaktere kadar (örn. `<AssemblyName>.dll`)

## <a name="examples"></a>Örnekler

Aşağıdaki komut derlemeyi `mydll.dll` genel derleme önbelleğine yükler.

```console
gacutil /i mydll.dll
```

Aşağıdaki komut, derleme `hello` için başvuru sayısı olmadığı sürece derlemeyi genel derleme önbelleğinden kaldırır.

```console
gacutil /u hello
```

Önceki komutun, derleme adı tam olarak belirtilmediği için derleme önbelleğinden birden fazla derleme kaldırabileceğine dikkat edin. Örneğin, her iki sürüm 1.0.0.0.0 ve 3.2.2.1 `hello` önbelleğe `gacutil /u hello` yüklenirse, komut her iki derlemeyi de kaldırır.

Birden fazla derlemeyi kaldırmayı önlemek için aşağıdaki örneği kullanın. Bu komut yalnızca `hello` tam olarak belirtilen sürüm numarası, kültür ve ortak anahtarla eşleşen derlemeyi kaldırır.

```console
gacutil /u hello, Version=1.0.0.1, Culture="de",PublicKeyToken=45e343aae32233ca
```

Aşağıdaki komut, dosyada `assemblyList.txt` belirtilen derlemeleri genel derleme önbelleğine yükler.

```console
gacutil /il assemblyList.txt
```

Aşağıdaki komut, dosyada `assemblyList.txt` belirtilen derlemeleri genel derleme önbelleğinden kaldırır.

```console
gacutil /ul assemblyList.txt
```

Aşağıdaki komut genel `myDll.dll` derleme önbelleğine yüklenir ve saymak için bir başvuru ekler. Derleme `myDll.dll` uygulama `MyApp`tarafından kullanılır. Parametre, Windows'ta `UNINSTALL_KEY MyApp` Programlar Ekle/Kaldır'a ekleyen `MyApp` kayıt defteri anahtarını belirtir. Açıklama parametresi olarak `My Application Description`belirtilir.

```console
gacutil /i /r myDll.dll UNINSTALL_KEY MyApp "My Application Description"
```

Aşağıdaki komut genel `myDll.dll` derleme önbelleğine yüklenir ve saymak için bir başvuru ekler. Şema `FILEPATH`parametresi, ve id `c:\applications\myApp\myApp.exe`parametresi, , yükleme `myDll.dll.` uygulamasına giden yolu belirtaçıklama parametresi olarak `MyApp`belirtilir.

```console
gacutil /i /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp
```

Aşağıdaki komut genel `myDll.dll` derleme önbelleğine yüklenir ve saymak için bir başvuru ekler. Şema parametresi, `OPAQUE`id ve açıklama parametrelerini özelleştirmenize olanak sağlar.

```console
gacutil /i /r mydll.dll OPAQUE "Insert custom application details here" "Insert Custom description information here"
```

Aşağıdaki komut, uygulama `myDll.dll` `myApp`tarafından başvuru kaldırır. Eğer bu, derleme için olan son başvuruysa, derlemeyi ayrıca genel bütünleştirilmiş kod önbelleğinden de kaldırır.

```console
gacutil /u /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp
```

Aşağıdaki komut genel bütünleştirilmiş kod önbelleğinin içeriğini listeler.

```console
gacutil /l
```

## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Genel Derleme Önbelleği](../app-domains/gac.md)
- [Regasm.exe (Derleme Kayıt Aracı)](regasm-exe-assembly-registration-tool.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
