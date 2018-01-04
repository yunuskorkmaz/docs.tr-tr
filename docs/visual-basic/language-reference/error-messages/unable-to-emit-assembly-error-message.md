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
ms.openlocfilehash: b19b6439d85822c69adac0b3e0e04b2f31299836
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a>Derleme oluşturulamıyor: &lt;hata iletisi&gt;
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Derleyici derleme oluşturma çıkması aşamasında hata raporlama bağlayıcı ile derleme bağlayıcı (bir derleme bir bildirim oluşturmak için Al.exe, Alink olarak da bilinir) çağırır.  
  
 **Hata Kimliği:** BC30145  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Tırnak işaretli hata iletisini inceleyin ve konu bakın [Al.exe](../../../framework/tools/al-exe-assembly-linker.md). Daha fazla açıklama ve öneriler için.  
  
2.  Derleme kullanarak el ile oturum açmayı deneyin [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) veya [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md).  
  
3.  Sorun devam ederse, koşullar hakkında bilgi toplayın ve Microsoft Ürün Destek Hizmetleri'ne bildirin.  
  
### <a name="to-sign-the-assembly-manually"></a>Derleme el ile imzalamak için  
  
1.  [Sn.exe (tanımlayıcı ad aracı)] kullanın[Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)) ortak/özel anahtar çifti dosya oluşturulamadı.  
  
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
 
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).  
 [Sn.exe (tanımlayıcı ad aracı)] [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md))  
 [Nasıl yapılır: Genel-Özel Anahtar Çifti Oluşturma](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [Bizimle İletişime Geçin](/visualstudio/ide/talk-to-us)
