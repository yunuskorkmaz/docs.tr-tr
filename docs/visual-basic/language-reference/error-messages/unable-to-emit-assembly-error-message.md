---
description: 'Şu konuda daha fazla bilgi edinin: BC30145: bütünleştirilmiş kod yayılamıyor: <error message>'
title: 'Derleme yayılamıyor: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 2ba476b39b6aa441d8778ee0618dcc3dcf3f7ac8
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653289"
---
# <a name="bc30145-unable-to-emit-assembly-error-message"></a>BC30145: bütünleştirilmiş kod yayılamıyor: \<error message>

Visual Basic derleyici, bildirime sahip bir derleme oluşturmak için derleme bağlayıcı (*Al.exe* ve Alink olarak da bilinir) çağırır ve bağlayıcı derlemeyi oluşturan egörev aşamasında bir hata bildiriyor.

**Hata kimliği:** BC30145

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Alıntı yapılan hata iletisini inceleyin ve daha fazla açıklama ve öneri için [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) konusuna başvurun.

2. [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) ya da [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)kullanarak derlemeyi el ile imzalamayı deneyin.

3. Hata devam ederse, koşullar hakkındaki bilgileri toplayın ve Microsoft Ürün Destek Hizmetleri 'ne bildirin.

### <a name="to-sign-the-assembly-manually"></a>Derlemeyi el ile imzalamak için

1. Ortak/özel anahtar çifti dosyası oluşturmak için [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)) kullanın.

   Bu dosya *. snk* uzantısına sahiptir.

2. Projenizden hatayı üreten COM başvurusunu silin.

3. [Visual studio Geliştirici komut istemi veya Visual Studio Geliştirici PowerShell](/visualstudio/ide/reference/command-prompt-powershell)'i açın.

4. Dizinini, derleme sarmalayıcıyı yerleştirmek istediğiniz dizine değiştirin.

5. Aşağıdaki komutu girin:

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   Girebileceğiniz gerçek komuta bir örnek:

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > Bir yol veya dosya boşluk içeriyorsa çift tırnak işareti kullanın.

6. Visual Studio 'da, yeni oluşturduğunuz dosyaya bir .NET derleme başvurusu ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)
- [Nasıl yapılır: Public-Private anahtar çifti oluşturma](../../../standard/assembly/create-public-private-key-pair.md)
- [Visual Studio geri bildirim seçenekleri](/visualstudio/ide/feedback-options)
