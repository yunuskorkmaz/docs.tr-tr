---
title: "Gacutil.exe (Genel Derleme Önbelleği Aracı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90c8a2467d48a45fe333cd07e34bca5ecfa5d727
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="gacutilexe-global-assembly-cache-tool"></a>Gacutil.exe (Genel Derleme Önbelleği Aracı)
Genel Bütünleştirilmiş Kod Önbelleği aracı genel bütünleştirilmiş kod önbelleğinin ve indirme önbelleğinin içeriğini görüntülemenize ve değiştirmenize olanak sağlar.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
gacutil [options] [assemblyName | assemblyPath | assemblyListFile]  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*assemblyName*|Bir derlemenin adı. Bir kısmen belirtilen derleme adı gibi sağlayabilir `myAssembly` veya belirtilen derlemenin tam adı gibi `myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5`.|  
|*assemblyPath*|Bir derleme bildirimi içeren dosyanın adı.|  
|*assemblyListFile*|Yüklenecek veya kaldırılacak derlemeleri listeleyen bir ANSI metin dosyasının yolu. Derlemeleri yüklemek üzere metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda yolu belirtin. Aracı göreli yollara, konumunu yorumlar *assemblyListFile*. Derlemeleri kaldırmak üzere bir metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda tam derleme adını belirtin. Bkz: *assemblyListFile* içeriği daha sonra bu konudaki örnekler.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/CDL**|İndirme önbelleğinin içeriğini siler.|  
|**/f**|Bu seçenek ile belirtin **/i** veya **/il** yeniden yüklemek için bir derleme zorlamak için Seçenekler. Eğer genel bütünleştirilmiş kod önbelleğinde aynı ada sahip bir derleme zaten bulunuyorsa, araç onun üzerine yazar.|  
|**/h**[**ardım**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/ı** *assemblyPath*|Genel bütünleştirilmiş kod önbelleğine bir derleme yükler.|  
|**/if***assemblyPath* |Genel bütünleştirilmiş kod önbelleğine bir derleme yükler. Eğer genel bütünleştirilmiş kod önbelleğinde aynı ada sahip bir derleme zaten bulunuyorsa, araç onun üzerine yazar.<br /><br /> Bu seçeneğin belirtilmesi belirtmeye eşdeğer **/i** ve **/f** birlikte seçenekleri.|  
|**/İl** *assemblyListFile*|Belirtilen bir veya daha fazla derlemeleri yükler *assemblyListFile* genel derleme önbelleğine.|  
|**/iR***assemblyPath* <br /><br /> *düzeni*<br /><br /> *Kimliği*<br /><br /> *Açıklama*|Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler ve derlemeyi saymak için bir başvuru ekler. Belirtmeniz gerekir *assemblyPath*, *düzeni*, *kimliği*, ve *açıklama* bu seçenekle parametreleri. Bu parametreler için belirtebilirsiniz geçerli değerler açıklaması için bkz: **/r** seçeneği.<br /><br /> Bu seçeneğin belirtilmesi belirtmeye eşdeğer **/i** ve **/r** birlikte seçenekleri.|  
|**/l** [*assemblyName*]|Genel bütünleştirilmiş kod önbelleğinin içeriğini listeler. Belirtirseniz *assemblyName* parametresi, aracı, yalnızca o adla eşleşen derlemeleri listeler.|  
|**/ldl**|İndirilen dosyalar önbelleğinin içeriğini listeler.|  
|**/lr** [*assemblyName*]|Tüm derlemeleri ve karşılık gelen başvuru sayılarını listeler. Belirtirseniz *assemblyName* parametresi, araç yalnızca adı eşleşen derlemeleri listeler ve bunların karşılık gelen başvuru sayar.|  
|**/ nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/r** [*assemblyName &#124; assemblyPath*]<br /><br /> *düzeni*<br /><br /> *Kimliği*<br /><br /> *Açıklama*|Yüklenecek veya kaldırılacak bir derleme veya derlemeler için izlenen bir başvuru belirtir. Bu seçenek ile belirtin **/i**, **/il**, **/u**, veya **/ul** seçenekleri.<br /><br /> Bir derlemeyi yüklemek için belirtmeniz *assemblyPath*, *düzeni*, *kimliği*, ve *açıklama* bu seçenekle parametreleri. Bir derlemeyi kaldırmak için belirtin *assemblyName*, *düzeni*, *kimliği*, ve *açıklama* parametreleri.<br /><br /> Derleme başvurusunu kaldırmak için aynı belirtmelisiniz *düzeni*, *kimliği*, ve *açıklama* ile belirtilen parametreleri **/i** ve **/r** (veya **/ir**) seçenekleri derleme yüklendiğinde. Eğer bir derlemeyi kaldırıyorsanız, eğer kaldırılacak son başvuruysa ve Windows Installer'ın o derlemeye hiçbir başvurusu yok ise araç derlemeyi genel bütünleştirilmiş kod önbelleğinden de kaldırır.<br /><br /> *Düzeni* parametresi yükleme düzeni türünü belirtir. Aşağıdaki değerlerden birini belirleyebilirsiniz.<br /><br /> -UNINSTALL_KEY: yükleyici Microsoft Windows'daki Program Ekle/Kaldır uygulamaya ekler, bu değeri belirtin. Uygulamalar HKLM\Software\Microsoft\Windows\CurrentVersion içine bir kayıt defteri anahtarı ekleyerek kendilerini Program Ekle/Kaldır'a ekler.<br />-FILEPATH: yükleyici Program Ekle/Kaldır uygulamaya eklemez, bu değeri belirtin.<br />-OPAK: bir kayıt defteri anahtarı sağlayarak, bu değeri belirtin veya dosya yolu yükleme senaryonuz için geçerli değildir. Bu değer için bir özel bilgiyi belirtmenize olanak tanır *kimliği* parametresi.<br /><br /> Belirtmek için değer *kimliği* parametresi için belirtilen değer bağımlı *düzeni* parametre:<br /><br /> -UNINSTALL_KEY için belirtirseniz, *düzeni* parametresi HKLM\Software\Microsoft\Windows\CurrentVersion kayıt defteri anahtarında ayarlama uygulamanın adını belirtin. Uygulamam için kayıt defteri anahtarı HKLM\Software\Microsoft\Windows\CurrentVersion\MyApp ise, örneğin, belirtin *kimliği* parametresi.<br />-İçin FILEPATH belirtirseniz, *düzeni* parametresi olarak derleme yükler yürütülebilir dosyanın tam yolunu belirtmeniz *kimliği* parametresi.<br />-İçin OPAK belirtirseniz, *düzeni* parametresi, herhangi bir parçası veri sağlamak *kimliği* parametresi. Belirttiğiniz veri tırnak işaretleri ("") arasına alınmalıdır.<br /><br /> *Açıklama* parametresi yüklemek için uygulamayla ilgili açıklayıcı metin belirtmenize olanak verir. Bu bilgi başvurular numaralandığında görüntülenir.|  
|**/silent**|Tüm çıktıların görüntülenmesini bastırır.|  
|**/u***assemblyName* |Genel bütünleştirilmiş kod önbelleğinden bir derlemeyi kaldırır.|  
|**/UF***assemblyName* |Belirtilen bir derlemenin tüm başvurularını kaldırarak derlemeyi kaldırmaya zorlar.<br /><br /> Bu seçeneğin belirtilmesi belirtmeye eşdeğer **/u** ve **/f** birlikte seçenekleri. **Not:** Microsoft Windows Installer kullanılarak yüklenmiş bir derlemeyi kaldırmak için bu seçeneği kullanamazsınız. Eğer bu işlemi yapmayı denerseniz, araç bir hata iletisi görüntüler.|  
|**/UL** *assemblyListFile*|Belirtilen bir veya daha fazla derlemeleri kaldırır *assemblyListFile* genel derleme önbelleğinden.|  
|**/u**[**ngen**] *assemblyName*|Belirtilen bir derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırır. Eğer belirtilen derlemenin varolan başvuru sayısı varsa, araç başvuru sayılarını görüntüler ve derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırmaz. **Not:** .NET Framework sürüm 2.0, `/ungen` desteklenmiyor. Bunun yerine, kullanın `uninstall` komutu [Ngen.exe (yerel Görüntü Oluşturucu)](../../../docs/framework/tools/ngen-exe-native-image-generator.md). <br /><br /> .NET Framework sürüm 1.0 ve 1.1 belirtme **/ ungen** derleme yerel görüntü önbellekten kaldırmak Gacutil.exe neden olur. Bu önbellek yerel görüntüler için kullanılarak oluşturulan derlemeleri depolar [Ngen.exe (yerel Görüntü Oluşturucu)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|  
|**/ur***assemblyName* <br /><br /> *düzeni*<br /><br /> *Kimliği*<br /><br /> *Açıklama*|Belirtilen bir derleme için genel bütünleştirilmiş kod önbelleğinden bir başvuru kaldırır. Derleme başvurusunu kaldırmak için aynı belirtmelisiniz *düzeni*, *kimliği*, ve *açıklama* ile belirtilen parametreleri **/i** ve **/r** (veya **/ir)** seçenekleri derleme yüklendiğinde. Bu parametreler için belirtebilirsiniz geçerli değerler açıklaması için bkz: **/r** seçeneği.<br /><br /> Bu seçeneğin belirtilmesi belirtmeye eşdeğer **/u** ve **/r** birlikte seçenekleri.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Gacutil.exe'yi kullanabilmek için yönetici ayrıcalıklarınız olmalıdır.  
  
 Özellikle, Gacutil.exe önbelleğe derlemeler yüklemenize, önbellekten derlemeleri kaldırmanıza ve önbelleğin içeriğini listelemenize olanak sağlar.  
  
 Gacutil.exe, Windows Installer tarafından desteklenen başvuru sayma düzenine benzer başvuru saymayı destekleyen seçenekler sağlar. Gacutil.exe'yi kullanarak aynı derlemeyi yükleyen iyi uygulamayı yükleyebilirsiniz: araç o derlemeye olan başvuruların sayısını takip eder. Sonuç olarak, derleme iki uygulama da kaldırılana kadar bilgisayarda kalır. Eğer Gacutil.exe'yi gerçek ürün yüklemelerinde kullanıyorsanız, başvuru saymayı destekleyen seçenekleri kullanın. Kullanım **/i** ve **/r** birlikte bir derleme yüklemek ve onu saymak için bir başvuru eklemek için Seçenekler. Kullanım **/u** ve **/r** birlikte bir derleme için bir başvuru sayısı kaldırmak için Seçenekler. Unutmayın, kullanarak **/i** ve **/u** seçenekleri tek başına başvuru sayımı desteklemez. Bu seçenekler uygulama geliştirme süresince kullanılmaya uygundur ancak gerçek ürün yüklemelerinde uygun değildir.  
  
 Kullanım **/il** veya **/ul** yüklemek veya bir ANSI metin dosyasında depolanan bir derleme listesi kaldırmak için Seçenekler. Metin dosyasının içeriği doğru şekilde biçimlendirilmelidir. Derlemeleri yüklemek üzere metin dosyası kullanmak için, dosyada her derleme için ayrı bir satırda yolu belirtin. Aşağıdaki örnek yüklenecek derlemeleri içeren bir dosyanın içeriğini gösterir.  
  
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
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komutu derlemeyi yükler `mydll.dll` genel derleme önbelleğine.  
  
```  
gacutil /i mydll.dll  
```  
  
 Aşağıdaki komut derleme kaldırır `hello` Genel Derleme Önbelleği hiçbir başvurusu sayar sürece mevcut derleme için.  
  
```  
gacutil /u hello  
```  
  
 Önceki komutun, derleme adı tam olarak belirtilmediği için derleme önbelleğinden birden fazla derleme kaldırabileceğine dikkat edin. Örneğin, her iki sürüm 1.0.0.0 ve 3.2.2.1, `hello` önbelleğe, komutu yüklü `gacutil /u hello` derlemeler her ikisi de kaldırır.  
  
 Birden fazla derlemeyi kaldırmayı önlemek için aşağıdaki örneği kullanın. Bu komut yalnızca kaldırır `hello` tam olarak belirtilen sürüm numarası, kültür ve ortak anahtar eşleşen derleme.  
  
```  
gacutil /u hello, Version=1.0.0.1, Culture="de",PublicKeyToken=45e343aae32233ca  
```  
  
 Aşağıdaki komut dosyasında belirtilen derlemeleri yükler `assemblyList.txt` genel derleme önbelleğine.  
  
 `gacutil /il assemblyList.txt`  
  
 Aşağıdaki komut dosyasında belirtilen derlemeleri kaldırır `assemblyList.txt` genel derleme önbelleğinden.  
  
 `gacutil /ul assemblyList.txt`  
  
 Aşağıdaki komut yükler `myDll.dll` genel derleme önbelleğine ve onu saymak için bir başvuru ekler. Derleme `myDll.dll` uygulama tarafından kullanılan `MyApp`. `UNINSTALL_KEY MyApp` Parametresi ekler kayıt defteri anahtarını belirtir `MyApp` için Windows'daki Program Ekle/Kaldır. Açıklama parametre olarak belirtilen `My Application Description`.  
  
```  
gacutil /i /r myDll.dll UNINSTALL_KEY MyApp "My Application Description"  
```  
  
 Aşağıdaki komut yükler `myDll.dll` genel derleme önbelleğine ve onu saymak için bir başvuru ekler. Şema parametresi `FILEPATH`ve ID parametresi `c:\applications\myApp\myApp.exe`, yüklüyor uygulama yolunu belirtin `myDll.dll.` açıklama parametre olarak belirtilen `MyApp`.  
  
 `gacutil /i /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp`  
  
 Aşağıdaki komut yükler `myDll.dll` genel derleme önbelleğine ve onu saymak için bir başvuru ekler. Şema parametresi `OPAQUE`, kimlik ve açıklama parametreleri özelleştirmenizi sağlar.  
  
```  
gacutil /i /r mydll.dll OPAQUE "Insert custom application details here" "Insert Custom description information here"  
```  
  
 Aşağıdaki komut başvurusunu kaldırır `myDll.dll` uygulama tarafından `myApp`. Eğer bu, derleme için olan son başvuruysa, derlemeyi ayrıca genel bütünleştirilmiş kod önbelleğinden de kaldırır.  
  
 `gacutil /u /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp`  
  
 Aşağıdaki komut genel bütünleştirilmiş kod önbelleğinin içeriğini listeler.  
  
```  
gacutil /l  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçları](../../../docs/framework/tools/index.md)  
 [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)  
 [RegAsm.exe (derleme kayıt aracı)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)  
 [Komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
