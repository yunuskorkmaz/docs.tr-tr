---
title: Lc.exe (Lisans Derleyici)
ms.date: 03/30/2017
helpviewer_keywords:
- Lc.exe
- .licx file
- License Compiler
- control licenses [Windows Forms]
- compiling licenses file
- license file
- .licenses file
- Windows Forms, control licenses
- licensed controls [Windows Forms]
ms.assetid: 2de803b8-495e-4982-b209-19a72aba0460
ms.openlocfilehash: 464514a241cc35fc821049ba0c29bec108d88253
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180404"
---
# <a name="lcexe-license-compiler"></a>Lc.exe (Lisans Derleyici)
Lisans Derleyicisi lisans bilgilerini içeren metin dosyalarını okur ve kaynak olarak bir ortak dil çalışma zamanı çalıştırılabilir dosyasının içinde katıştırılabilir bir ikili dosya oluşturur.  
  
 Bir .licx metin dosyası otomatik olarak üretilir veya forma lisanslı bir denetim eklendiğinde Windows Form Tasarlayıcısı tarafından güncelleştirilir. Derlemenin parçası olarak, proje sistemi .licx metin dosyasını .NET kontrol lisanslaması için destek sağlayan bir .licenses ikili kaynağına dönüştürür. İkili kaynak daha sonra proje çıktısına gömülecektir.  
  
 Projenizi oluştururken Lisans Derleyicisi'ni kullandığınızda, 32 bit ve 64 arasında çapraz derleme desteklenmez. Bunun nedeni, Lisans Derleyicisi'nin derlemeler yüklemek zorunda olması ve 64 bit derlemelerin 32 bit'lik bir uygulamadan yüklenmesine veya bunun tersinin yapılmasına izin verilmemesidir. Bu durumda, lisansı el ile derlemek için Lisans Derleyicisi'ni komut satırından kullanın ilgili mimariyi belirtin.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console
      lc /target:  
targetPE /complist:filename [-outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/complist:** *dosya adı*|.licenses dosyasına eklenecek lisanslı bileşenlerin listesini içeren dosyanın adını belirtin. Her bir bileşene, her satırda yalnızca bir bileşen olacak şekilde, bileşenin tam adı kullanılarak başvurulur.<br /><br /> Komut satırı kullanıcıları projedeki her bir form için ayrı bir dosya belirtebilir. Lc.exe birden çok giriş dosyasını kabul eder ve tek bir .licenses dosyası üretir.|  
|**/h**[**elp**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/i:** *modül*|**/complist** dosyasında listelenen bileşenleri içeren modülleri belirtir. Birden fazla modül belirtmek için birden çok **/i** bayrak kullanın.|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/outdir:** *yol*|Çıkış .licenses dosyasının yerleştirileceği dizin belirtir.|  
|**/target:** *targetPE*|.licenses dosyasının kendisi için üretilmekte olduğu yürütülebilir dosyayı belirtir.|  
|**/v**|Ayrıntılı modu belirtir; derleme ilerleme bilgilerini görüntüler.|  
|**@***dosya*|Yanıt (.rsp) dosyasını belirtir.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="example"></a>Örnek  
  
1. Adlı `HostApp.exe`bir uygulamada bulunan `MyCompany.Samples.LicControl1` `Samples.DLL` lisanslı bir denetim kullanıyorsanız, `HostAppLic.txt` aşağıdakileri içeren oluşturabilirsiniz. *,*  
  
    ```text
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. Aşağıdaki komutu kullanarak `HostApp.exe.licenses` .licenses dosyasını oluşturun.  
  
    ```console  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. .licenses dosyasını kaynak olarak `HostApp.exe` içeren yapı oluşturun. Bir C# uygulaması oluşturuyorsanız, uygulamanızı oluşturmak için aşağıdaki komutu kullanırsınız.  
  
    ```console
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 Aşağıdaki komut, `myApp.licenses` tarafından `hostapplic.txt` `hostapplic2.txt` belirtilen lisanslı bileşenlerin listelerinden derler ve `hostapplic3.txt`. Bağımsız `modulesList` değişken, lisanslı bileşenleri içeren modülleri belirtir.  
  
```console  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a>Yanıt Dosyası Örneği  
 Aşağıdaki liste, `response.rsp`bir yanıt dosyasının örneğini gösterir. Yanıt dosyaları hakkında daha fazla bilgi için [Yanıt Dosyaları'na](/visualstudio/msbuild/msbuild-response-files)bakın.  
  
```text  
/target:hostapp.exe  
/complist:hostapplic.txt
/i:WFCPrj.dll
/outdir:"C:\My Folder"  
```  
  
 Aşağıdaki komut satırı `response.rsp` dosyayı kullanır.  
  
```console  
lc @response.rsp  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](al-exe-assembly-linker.md)
- [Komut İstemleri](developer-command-prompt-for-vs.md)
