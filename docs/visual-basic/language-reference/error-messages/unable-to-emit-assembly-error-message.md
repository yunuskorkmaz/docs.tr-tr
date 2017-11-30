---
title: "Derleme oluşturulamıyor: &lt;hata iletisi&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords: BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9dcf3d4bec379faa5783ca17847b91f9739df598
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a>Derleme oluşturulamıyor: &lt;hata iletisi&gt;
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Derleyici derleme oluşturma çıkması aşamasında hata raporlama bağlayıcı ile derleme bağlayıcı (bir derleme bir bildirim oluşturmak için Al.exe, Alink olarak da bilinir) çağırır.  
  
 **Hata Kimliği:** BC30145  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Tırnak işaretli hata iletisini inceleyin ve konu bakın [Al.exe aracı hataları ve Uyarıları](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) daha ayrıntılı bir açıklama ve öneriler için.  
  
2.  Derleme kullanarak el ile oturum açmayı deneyin [Al.exe (derleme bağlayıcı)](https://msdn.microsoft.com/library/c405shex) veya [Sn.exe (tanımlayıcı ad aracı)](https://msdn.microsoft.com/library/k5b5tt23).  
  
3.  Sorun devam ederse, koşullar hakkında bilgi toplayın ve Microsoft Ürün Destek Hizmetleri'ne bildirin.  
  
### <a name="to-sign-the-assembly-manually"></a>Derleme el ile imzalamak için  
  
1.  Kullanım [Sn.exe (tanımlayıcı ad aracı)](https://msdn.microsoft.com/library/k5b5tt23) ortak/özel anahtar çifti dosya oluşturulamadı.  
  
     Bu dosya .snk uzantısına sahiptir.  
  
2.  Projenizden hata oluşturmadan COM başvurusu silin.  
  
3.  Windows **Başlat** menüsündeki **programları**, işaret **Microsoft Visual Studio 2008**, işaret **Visual Studio Araçları**, ve ardından **Visual Studio 2008 Komut İstemi**.  
  
4.  Derleme sarmalayıcı eklemek istediğiniz yeri dizinine taşıyın.  
  
5.  Aşağıdaki kodu yazın.  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     Girdiğiniz kod örneği aşağıdaki gibi olabilir.  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     Bir yol veya dosya boşluk içeriyorsa, çift tırnak işaretleri (") kullanın.  
  
6.  İçinde [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], yeni oluşturduğunuz dosyayı bir .NET derlemesi başvuru ekleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Al.exe (derleme bağlayıcı)](https://msdn.microsoft.com/library/c405shex)  
 [Al.exe aracı hataları ve Uyarıları](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [Sn.exe (tanımlayıcı ad aracı)](https://msdn.microsoft.com/library/k5b5tt23)  
 [Nasıl yapılır: bir genel-özel anahtar çifti oluşturma](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114)  
 [Bizimle iletişime geçin](/visualstudio/ide/talk-to-us)
