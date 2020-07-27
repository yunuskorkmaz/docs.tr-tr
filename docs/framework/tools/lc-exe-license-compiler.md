---
title: Lc.exe (Lisans Derleyici)
description: Lisans derleyicisini Lc.exe kullanın. Bu araç lisanslama bilgilerine sahip metin dosyalarını okur ve bir CLR yürütülebilirini kaynak olarak eklemek için bir ikili dosya oluşturur.
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
ms.openlocfilehash: 45a80ba7c3e24c0f419758315b2d2daafd3890f4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164246"
---
# <a name="lcexe-license-compiler"></a>Lc.exe (Lisans Derleyici)
Lisans Derleyicisi lisans bilgilerini içeren metin dosyalarını okur ve kaynak olarak bir ortak dil çalışma zamanı çalıştırılabilir dosyasının içinde katıştırılabilir bir ikili dosya oluşturur.  
  
 Bir .licx metin dosyası otomatik olarak üretilir veya forma lisanslı bir denetim eklendiğinde Windows Form Tasarlayıcısı tarafından güncelleştirilir. Derlemenin parçası olarak, proje sistemi .licx metin dosyasını .NET kontrol lisanslaması için destek sağlayan bir .licenses ikili kaynağına dönüştürür. İkili kaynak daha sonra proje çıktısına gömülecektir.  
  
 Projenizi oluştururken Lisans Derleyicisi'ni kullandığınızda, 32 bit ve 64 arasında çapraz derleme desteklenmez. Bunun nedeni, Lisans Derleyicisi'nin derlemeler yüklemek zorunda olması ve 64 bit derlemelerin 32 bit'lik bir uygulamadan yüklenmesine veya bunun tersinin yapılmasına izin verilmemesidir. Bu durumda, lisansı el ile derlemek için Lisans Derleyicisi'ni komut satırından kullanın ilgili mimariyi belirtin.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Sözdizimi  
  
```console
      lc /target:  
targetPE /complist:filename [-outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/complist:** *filename*|.licenses dosyasına eklenecek lisanslı bileşenlerin listesini içeren dosyanın adını belirtin. Her bir bileşene, her satırda yalnızca bir bileşen olacak şekilde, bileşenin tam adı kullanılarak başvurulur.<br /><br /> Komut satırı kullanıcıları projedeki her bir form için ayrı bir dosya belirtebilir. Lc.exe birden çok giriş dosyasını kabul eder ve tek bir .licenses dosyası üretir.|  
|**/h**[**ELP**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/i:** *module*|**/Complist** dosyasında listelenen bileşenleri içeren modülleri belirtir. Birden fazla modül belirtmek için birden çok **/i** bayrağı kullanın.|  
|**/nologo**|Microsoft başlangıç başlığı görüntüsünü bastırır.|  
|**/OutDir:** *yol*|Çıkış .licenses dosyasının yerleştirileceği dizin belirtir.|  
|**/target:** *targetpe*|.licenses dosyasının kendisi için üretilmekte olduğu yürütülebilir dosyayı belirtir.|  
|**çıktıda**|Ayrıntılı modu belirtir; derleme ilerleme bilgilerini görüntüler.|  
|**@***Dosya*|Yanıt (. rsp) dosyasını belirtir.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="example"></a>Örnek  
  
1. Adlı bir uygulamada bulunan lisanslı bir denetim kullanıyorsanız `MyCompany.Samples.LicControl1` `Samples.DLL` `HostApp.exe` *,* `HostAppLic.txt` aşağıdakileri içeren oluşturabilirsiniz.  
  
    ```text
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. Aşağıdaki komutu kullanarak adlı. lisansları dosyasını oluşturun `HostApp.exe.licenses` .  
  
    ```console  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. `HostApp.exe`. Lisanslar dosyasını kaynak olarak içeren derleme. Bir C# uygulaması oluşturuyorsanız, uygulamanızı oluşturmak için aşağıdaki komutu kullanırsınız.  
  
    ```console
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 Aşağıdaki komut `myApp.licenses` , ve tarafından belirtilen lisanslı bileşenler listesinden derlenir `hostapplic.txt` `hostapplic2.txt` `hostapplic3.txt` . `modulesList`Bağımsız değişkeni, lisanslı bileşenleri içeren modülleri belirtir.  
  
```console  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a>Yanıt dosyası örneği  
 Aşağıdaki listede bir yanıt dosyası örneği gösterilmektedir `response.rsp` . Yanıt dosyaları hakkında daha fazla bilgi için bkz. [yanıt dosyaları](/visualstudio/msbuild/msbuild-response-files).  
  
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
- [Al.exe (bütünleştirilmiş kod bağlayıcı)](al-exe-assembly-linker.md)
- [Komut Istemleri](developer-command-prompt-for-vs.md)
