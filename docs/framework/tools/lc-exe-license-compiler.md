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
ms.openlocfilehash: c5a8b38e819c323a06faad2edba586cb18d26edc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="lcexe-license-compiler"></a>Lc.exe (Lisans Derleyici)
Lisans Derleyicisi lisans bilgilerini içeren metin dosyalarını okur ve kaynak olarak bir ortak dil çalışma zamanı çalıştırılabilir dosyasının içinde katıştırılabilir bir ikili dosya oluşturur.  
  
 Bir .licx metin dosyası otomatik olarak üretilir veya forma lisanslı bir denetim eklendiğinde Windows Form Tasarlayıcısı tarafından güncelleştirilir. Derlemenin parçası olarak, proje sistemi .licx metin dosyasını .NET kontrol lisanslaması için destek sağlayan bir .licenses ikili kaynağına dönüştürür. İkili kaynak daha sonra proje çıktısına gömülecektir.  
  
 Projenizi oluştururken Lisans Derleyicisi'ni kullandığınızda, 32 bit ve 64 arasında çapraz derleme desteklenmez. Bunun nedeni, Lisans Derleyicisi'nin derlemeler yüklemek zorunda olması ve 64 bit derlemelerin 32 bit'lik bir uygulamadan yüklenmesine veya bunun tersinin yapılmasına izin verilmemesidir. Bu durumda, lisansı el ile derlemek için Lisans Derleyicisi'ni komut satırından kullanın ilgili mimariyi belirtin.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın. Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
      lc /target:  
      targetPE /complist:filename [/outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/complist:** *dosya adı*|.licenses dosyasına eklenecek lisanslı bileşenlerin listesini içeren dosyanın adını belirtin. Her bir bileşene, her satırda yalnızca bir bileşen olacak şekilde, bileşenin tam adı kullanılarak başvurulur.<br /><br /> Komut satırı kullanıcıları projedeki her bir form için ayrı bir dosya belirtebilir. Lc.exe birden çok giriş dosyasını kabul eder ve tek bir .licenses dosyası üretir.|  
|**/h**[**ardım**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**i:** *Modülü*|Listelenen bileşenleri içeren modüllerin belirtir **/complist** dosya. Birden fazla modülü belirtmek için birden çok kullanın **/i** bayrakları.|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**OutDir:** *yolu*|Çıkış .licenses dosyasının yerleştirileceği dizin belirtir.|  
|**/ target:** *targetPE*|.licenses dosyasının kendisi için üretilmekte olduğu yürütülebilir dosyayı belirtir.|  
|**/v**|Ayrıntılı modu belirtir; derleme ilerleme bilgilerini görüntüler.|  
|**@** *Dosya*|Yanıt (.rsp) dosyasını belirtir.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="example"></a>Örnek  
  
1.  Lisanslı denetim kullanıyorsanız `MyCompany.Samples.LicControl1` içinde yer alan `Samples.DLL` adlı bir uygulamada `HostApp.exe` *,* oluşturabileceğiniz `HostAppLic.txt` aşağıdakileri içerir.  
  
    ```  
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2.  Adlı .licenses dosyası oluşturun `HostApp.exe.licenses` aşağıdaki komutu kullanarak.  
  
    ```  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3.  Yapı `HostApp.exe` bir kaynak olarak .licenses dosyası dahil olmak üzere. Bir C# uygulaması oluşturuyorsanız, uygulamanızı oluşturmak için aşağıdaki komutu kullanırsınız.  
  
    ```  
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 Aşağıdaki komut derlerken `myApp.licenses` tarafından belirtilen lisanslı bileşenlerinin listelerden `hostapplic.txt`, `hostapplic2.txt` ve `hostapplic3.txt`. `modulesList` Bağımsız değişkeni lisanslı bileşenlerini içeren modüllerin belirtir.  
  
```  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a>Yanıt dosyası örneği  
 Aşağıdaki liste bir yanıt dosyası örneği gösterilmektedir `response.rsp`. Yanıt dosyaları hakkında daha fazla bilgi için bkz: [yanıt dosyaları](/visualstudio/msbuild/msbuild-response-files).  
  
```  
/target:hostapp.exe  
/complist:hostapplic.txt   
/i:WFCPrj.dll   
/outdir:"C:\My Folder"  
```  
  
 Aşağıdaki komut satırı kullandığı `response.rsp` dosya.  
  
```  
lc @response.rsp  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araçlar](../../../docs/framework/tools/index.md)  
 [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [Komut İstemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
