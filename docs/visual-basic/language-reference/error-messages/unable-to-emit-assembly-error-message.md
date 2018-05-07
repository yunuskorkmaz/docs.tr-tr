---
title: 'Derleme oluşturulamıyor: &lt;hata iletisi&gt;'
ms.date: 07/20/2015
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 8f497069088ad30a3be58d02caa0a32f7f1b21b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a>Derleme oluşturulamıyor: &lt;hata iletisi&gt;
Visual Basic derleyici derleme oluşturma çıkması aşamasında hata raporlama bağlayıcı ile derleme bağlayıcı (bir derleme bir bildirim oluşturmak için Al.exe, Alink olarak da bilinir) çağırır.  
  
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
  
6.  Visual Studio'da yeni oluşturduğunuz dosyayı bir .NET derlemesi başvuru ekleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).  
 [Sn.exe (tanımlayıcı ad aracı)] [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md))  
 [Nasıl yapılır: Genel-Özel Anahtar Çifti Oluşturma](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [Bizimle İletişime Geçin](/visualstudio/ide/talk-to-us)
