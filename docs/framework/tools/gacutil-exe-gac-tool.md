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
ms.openlocfilehash: 437d2d1bb026795dfa01a4c01ca12acf2b8f5792
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044663"
---
# <a name="gacutilexe-global-assembly-cache-tool"></a>Gacutil.exe (Genel Derleme Önbelleği Aracı)

Genel Bütünleştirilmiş Kod Önbelleği aracı genel bütünleştirilmiş kod önbelleğinin ve indirme önbelleğinin içeriğini görüntülemenize ve değiştirmenize olanak sağlar.

Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).

Komut satırına şunu yazın:

## <a name="syntax"></a>Sözdizimi

```console
gacutil [options] [assemblyName | assemblyPath | assemblyListFile]
```

## <a name="parameters"></a>Parametreler

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|*assemblyName*|Bir derlemenin adı. Gibi kısmen belirtilen bir derleme adı `myAssembly` ya da gibi tam olarak belirtilen bir derleme `myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5`adı sağlayabilirsiniz.|
|*assemblyPath*|Bir derleme bildirimi içeren dosyanın adı.|
|*assemblyListFile*|Yüklenecek veya kaldırılacak derlemeleri listeleyen bir ANSI metin dosyasının yolu. Derlemeleri yüklemek üzere metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda yolu belirtin. Araç, *AssemblyListFile*konumuna göre göreli yolları yorumlar. Derlemeleri kaldırmak üzere bir metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda tam derleme adını belirtin. Bu konunun ilerleyen kısımlarında *AssemblyListFile* içerik örneklerine bakın.|

|Seçenek|Açıklama|
|------------|-----------------|
|**/CDL**|İndirme önbelleğinin içeriğini siler.|
|**/f**|Bir derlemeyi yeniden yüklemeye zorlamak için bu seçeneği **/ı** veya **/Il** seçenekleriyle belirtin. Eğer genel bütünleştirilmiş kod önbelleğinde aynı ada sahip bir derleme zaten bulunuyorsa, araç onun üzerine yazar.|
|**/h** [**ELP**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|**/ı** *assemblyPath*|Genel bütünleştirilmiş kod önbelleğine bir derleme yükler.|
|**/if** *assemblyPath*|Genel bütünleştirilmiş kod önbelleğine bir derleme yükler. Eğer genel bütünleştirilmiş kod önbelleğinde aynı ada sahip bir derleme zaten bulunuyorsa, araç onun üzerine yazar.<br /><br /> Bu seçeneği belirtmek, **/i** ve **/f** seçeneklerini birlikte belirtmeye eşdeğerdir.|
|**/Il** *AssemblyListFile*|*AssemblyListFile* içinde belirtilen bir veya daha fazla derlemeyi genel bütünleştirilmiş kod önbelleğine yükleme.|
|**Description** *assemblyPath*<br /><br /> *Şemadaki*<br /><br /> *id*<br /><br /> *description*|Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler ve derlemeyi saymak için bir başvuru ekler. Bu seçenekle *assemblyPath*, *Scheme*, *ID*ve *Description* parametrelerini belirtmeniz gerekir. Bu parametreler için belirtebileceğiniz geçerli değerlerin bir açıklaması için **/r** seçeneğine bakın.<br /><br /> Bu seçeneği belirtmek, **/i** ve **/r** seçeneklerini birlikte belirtmeye eşdeğerdir.|
|**/l** [*AssemblyName*]|Genel bütünleştirilmiş kod önbelleğinin içeriğini listeler. *AssemblyName* parametresini belirtirseniz, araç yalnızca o adla eşleşen derlemeleri listeler.|
|**/LDL**|İndirilen dosyalar önbelleğinin içeriğini listeler.|
|**/LR** [*AssemblyName*]|Tüm derlemeleri ve karşılık gelen başvuru sayılarını listeler. *AssemblyName* parametresini belirtirseniz, araç yalnızca o adla eşleşen derlemeleri ve bunlara karşılık gelen başvuru sayılarını listeler.|
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|
|**/r** [*AssemblyName &#124; assemblyPath*]<br /><br /> *Şemadaki*<br /><br /> *id*<br /><br /> *description*|Yüklenecek veya kaldırılacak bir derleme veya derlemeler için izlenen bir başvuru belirtir. **/I**, **/Il**, **/u**veya **/ul** seçenekleriyle bu seçeneği belirtin.<br /><br /> Bir derlemeyi yüklemek için, bu seçenekle *assemblyPath*, *Scheme*, *ID*ve *Description* parametrelerini belirtin. Bir derlemeyi kaldırmak için *AssemblyName*, *Scheme*, *ID*ve *Description* parametrelerini belirtin.<br /><br /> Bir derlemeye yönelik bir başvuruyu kaldırmak için, derleme yüklenirken **/i** ve **/r** (veya **/ir**) seçenekleriyle belirtilen aynı *Düzen*, *kimlik*ve *Açıklama* parametrelerini belirtmeniz gerekir. Eğer bir derlemeyi kaldırıyorsanız, eğer kaldırılacak son başvuruysa ve Windows Installer'ın o derlemeye hiçbir başvurusu yok ise araç derlemeyi genel bütünleştirilmiş kod önbelleğinden de kaldırır.<br /><br /> *Scheme* parametresi, yükleme düzeninin türünü belirtir. Aşağıdaki değerlerden birini belirleyebilirsiniz.<br /><br /> - UNINSTALL_KEY: Yükleyici uygulamayı Microsoft Windows 'da Program Ekle/Kaldır 'a eklerse bu değeri belirtin. Uygulamalar HKLM\Software\Microsoft\Windows\CurrentVersion içine bir kayıt defteri anahtarı ekleyerek kendilerini Program Ekle/Kaldır'a ekler.<br />NULL Yükleyici uygulamayı Program Ekle/Kaldır 'a eklememezse bu değeri belirtin.<br />Ş Bir kayıt defteri anahtarı sağlamak veya yükleme senaryonuz için dosya yolu uygulanmadığından bu değeri belirtin. Bu değer, *ID* parametresi için özel bilgi belirtmenize olanak tanır.<br /><br /> *ID* parametresi için belirtme değeri, *Düzen* parametresi için belirtilen değere bağlıdır:<br /><br /> - *Scheme* PARAMETRESI için UNINSTALL_KEY belirtirseniz, HKLM\Software\Microsoft\Windows\CurrentVersion kayıt defteri anahtarında ayarlanan uygulamanın adını belirtin. Örneğin, kayıt defteri anahtarı HKLM\Software\Microsoft\Windows\CurrentVersion\MyApp ise *ID* parametresi için MyApp ' i belirtin.<br />- *Düzen* PARAMETRESI için FILEPATH belirtirseniz, derlemeyi *ID* parametresi olarak yükleyen yürütülebilir dosyanın tam yolunu belirtin.<br />- *Düzen* PARAMETRESI için donuk belirtirseniz, herhangi bir veri parçasını *ID* parametresi olarak sağlayabilirsiniz. Belirttiğiniz veri tırnak işaretleri ("") arasına alınmalıdır.<br /><br /> *Description* parametresi, yüklenecek uygulama hakkında açıklayıcı bir metin belirtmenize olanak tanır. Bu bilgi başvurular numaralandığında görüntülenir.|
|**/silent**|Tüm çıktıların görüntülenmesini bastırır.|
|**/u** *assemblyName*|Genel bütünleştirilmiş kod önbelleğinden bir derlemeyi kaldırır.|
|**/UF** *assemblyName*|Belirtilen bir derlemenin tüm başvurularını kaldırarak derlemeyi kaldırmaya zorlar.<br /><br /> Bu seçeneği belirtmek, **/u** ve **/f** seçeneklerini birlikte belirtmeye eşdeğerdir. **Not:**  Bu seçeneği, Microsoft Windows Installer kullanarak yüklenen bir derlemeyi kaldırmak için kullanamazsınız. Eğer bu işlemi yapmayı denerseniz, araç bir hata iletisi görüntüler.|
|**/ul** *AssemblyListFile*|*AssemblyListFile* içinde belirtilen bir veya daha fazla derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırır.|
|**/u** [**Ngen**] *AssemblyName*|Belirtilen bir derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırır. Eğer belirtilen derlemenin varolan başvuru sayısı varsa, araç başvuru sayılarını görüntüler ve derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırmaz. **Not:**  .NET Framework sürüm 2,0 ' `/ungen` de desteklenmez. Bunun yerine, `uninstall` [Ngen. exe (yerel görüntü Oluşturucu)](ngen-exe-native-image-generator.md)komutunu kullanın. <br /><br /> 1,0 ve 1,1 .NET Framework sürümlerinde, **/ungen** belirtildiğinde, derlemeyi yerel görüntü önbelleğinden kaldırmak Için Gacutil. exe neden olur. Bu önbellek, [Ngen. exe (yerel görüntü Oluşturucu)](ngen-exe-native-image-generator.md)kullanılarak oluşturulmuş derlemelerin yerel görüntülerini depolar.|
|**/ur** *assemblyName*<br /><br /> *Şemadaki*<br /><br /> *id*<br /><br /> *description*|Belirtilen bir derleme için genel bütünleştirilmiş kod önbelleğinden bir başvuru kaldırır. Bir derlemeye yönelik bir başvuruyu kaldırmak için, derleme yüklenirken **/i** ve **/r** (veya **/ir)** seçenekleriyle belirtilen aynı *Düzen*, *kimlik*ve *Açıklama* parametrelerini belirtmeniz gerekir. Bu parametreler için belirtebileceğiniz geçerli değerlerin bir açıklaması için **/r** seçeneğine bakın.<br /><br /> Bu seçeneği belirtmek, **/u** ve **/r** seçeneklerini birlikte belirtmeye eşdeğerdir.|
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|

## <a name="remarks"></a>Açıklamalar

> [!NOTE]
> Gacutil.exe'yi kullanabilmek için yönetici ayrıcalıklarınız olmalıdır.

Özellikle, Gacutil.exe önbelleğe derlemeler yüklemenize, önbellekten derlemeleri kaldırmanıza ve önbelleğin içeriğini listelemenize olanak sağlar.

Gacutil.exe, Windows Installer tarafından desteklenen başvuru sayma düzenine benzer başvuru saymayı destekleyen seçenekler sağlar. Gacutil.exe'yi kullanarak aynı derlemeyi yükleyen iyi uygulamayı yükleyebilirsiniz: araç o derlemeye olan başvuruların sayısını takip eder. Sonuç olarak, derleme iki uygulama da kaldırılana kadar bilgisayarda kalır. Eğer Gacutil.exe'yi gerçek ürün yüklemelerinde kullanıyorsanız, başvuru saymayı destekleyen seçenekleri kullanın. Bir derlemeyi yüklemek ve saymak için bir başvuru eklemek için **/i** ve **/r** seçeneklerini birlikte kullanın. Bir derlemenin başvuru sayısını kaldırmak için **/u** ve **/r** seçeneklerini birlikte kullanın. Yalnızca **/ı** ve **/u** seçeneklerinin kullanılması, başvuru saymayı desteklememe durumunu unutmayın. Bu seçenekler uygulama geliştirme süresince kullanılmaya uygundur ancak gerçek ürün yüklemelerinde uygun değildir.

Bir ANSI metin dosyasında depolanan derlemelerin listesini yüklemek veya kaldırmak için **/İl** veya **/ul** seçeneklerini kullanın. Metin dosyasının içeriği doğru şekilde biçimlendirilmelidir. Derlemeleri yüklemek üzere metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda yolu belirtin. Aşağıdaki örnek yüklenecek derlemeleri içeren bir dosyanın içeriğini gösterir.

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
> 79 ve 91 karakterlerinden (dosya uzantısı hariç) daha uzun bir dosya adı ile derleme yüklenmeye çalışılması aşağıdaki hatayla sonuçlanabilir:
>
> ```output
> Failure adding assembly to the cache:   The file name is too long.
> ```
>
> Bunun nedeni, dahili bir Gacutil. exe ' nin aşağıdaki öğelerden oluşan en fazla MAX_PATH karakterden oluşan bir yol oluşturur:
>
> - GAC root-34 karakterleri (IE. `C:\Windows\Microsoft.NET\assembly\`)
> - Mimari-7 veya 9 karakter (IE. `GAC_32\`, `GAC_64\`, `GAC_MSIL`)
> - Diğer öğelerin boyutuna bağlı olarak, en fazla 91 karakter olan AssemblyName (örn. `System.Xml.Linq\`)
> - AssemblyInfo-31-48 karakter veya daha fazlası:
>   - Framework-5 karakter (örn. `v4.0_`)
>   - AssemblyVersion-8 ile 24 karakter (örn. `9.0.1000.0_`)
>   - AssemblyLanguage-1 ile 8 karakter (örn. `de_`, `sr-Cyrl_`)
>   - PublicKey-17 karakter (örn. `31bf3856ad364e35\`)
> - DllFileName-91 + 4 karakter (IE). `<AssemblyName>.dll`)

## <a name="examples"></a>Örnekler

Aşağıdaki komut, derlemeyi `mydll.dll` genel derleme önbelleğine yüklenir.

```console
gacutil /i mydll.dll
```

Aşağıdaki komut, derleme için başvuru `hello` sayısı bulunmadığı sürece derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırır.

```console
gacutil /u hello
```

Önceki komutun, derleme adı tam olarak belirtilmediği için derleme önbelleğinden birden fazla derleme kaldırabileceğine dikkat edin. Örneğin, hem 1.0.0.0 hem de 3.2.2.1 of `hello` sürümü önbellekte yüklüyse, komut `gacutil /u hello` her iki derlemeyi de kaldırır.

Birden fazla derlemeyi kaldırmayı önlemek için aşağıdaki örneği kullanın. Bu komut yalnızca `hello` tam olarak belirtilen sürüm numarası, kültür ve ortak anahtarla eşleşen derlemeyi kaldırır.

```console
gacutil /u hello, Version=1.0.0.1, Culture="de",PublicKeyToken=45e343aae32233ca
```

Aşağıdaki komut, dosyasında `assemblyList.txt` belirtilen derlemeleri genel bütünleştirilmiş kod önbelleğine yüklenir.

```console
gacutil /il assemblyList.txt
```

Aşağıdaki komut, dosyasında `assemblyList.txt` belirtilen derlemeleri genel bütünleştirilmiş kod önbelleğinden kaldırır.

```console
gacutil /ul assemblyList.txt
```

Aşağıdaki komut genel derleme `myDll.dll` önbelleğine yüklenir ve saymak için bir başvuru ekler. Derleme `myDll.dll` , uygulama `MyApp`tarafından kullanılır. Parametresi, Windows 'da Program Ekle/Kaldır `MyApp` 'a ekleyen kayıt defteri anahtarını belirtir. `UNINSTALL_KEY MyApp` Description parametresi olarak `My Application Description`belirtilir.

```console
gacutil /i /r myDll.dll UNINSTALL_KEY MyApp "My Application Description"
```

Aşağıdaki komut genel derleme `myDll.dll` önbelleğine yüklenir ve saymak için bir başvuru ekler. Düzen parametresi `FILEPATH`, ve ID `c:\applications\myApp\myApp.exe`parametresi, açıklama parametresini `MyApp`yükleyen `myDll.dll.` uygulamanın yolunu belirtin.

```console
gacutil /i /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp
```

Aşağıdaki komut genel derleme `myDll.dll` önbelleğine yüklenir ve saymak için bir başvuru ekler. Düzen parametresi `OPAQUE`, kimlik ve açıklama parametrelerini özelleştirmenize olanak sağlar.

```console
gacutil /i /r mydll.dll OPAQUE "Insert custom application details here" "Insert Custom description information here"
```

Aşağıdaki komut, başvurusunu `myDll.dll` uygulama `myApp`tarafından kaldırır. Eğer bu, derleme için olan son başvuruysa, derlemeyi ayrıca genel bütünleştirilmiş kod önbelleğinden de kaldırır.

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
