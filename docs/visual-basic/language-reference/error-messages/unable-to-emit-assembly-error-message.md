---
title: 'Derleme yayılamıyor: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 530aaee40be92bf72ee4b83b4141108e9b81c8a1
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70968860"
---
# <a name="unable-to-emit-assembly-error-message"></a>Bütünleştirilmiş kod yayılamıyor: \<hata iletisi >

Visual Basic derleyici, bildirime sahip bir derleme oluşturmak için derleme Bağlayıcısı (*al. exe*, ve Alink olarak da bilinir) çağırır ve bağlayıcı derlemeyi oluşturan egörev aşamasında bir hata bildiriyor.

**Hata KIMLIĞI:** BC30145

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Alıntı yapılan hata iletisini inceleyin ve daha fazla açıklama ve öneri için [al. exe](../../../framework/tools/al-exe-assembly-linker.md) konusuna başvurun.

2. [Al. exe](../../../framework/tools/al-exe-assembly-linker.md) veya [sn. exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)kullanarak derlemeyi el ile imzalamayı deneyin.

3. Hata devam ederse, koşullar hakkındaki bilgileri toplayın ve Microsoft Ürün Destek Hizmetleri 'ne bildirin.

### <a name="to-sign-the-assembly-manually"></a>Derlemeyi el ile imzalamak için

1. Bir ortak/özel anahtar çifti dosyası oluşturmak için [sn. exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)öğesini kullanın.

   Bu dosya *. snk* uzantısına sahiptir.

2. Projenizden hatayı üreten COM başvurusunu silin.

3. [Visual Studio için geliştirici komut istemi](../../../framework/tools/developer-command-prompt-for-vs.md)açın.

   Windows 10 ' da, görev çubuğundaki arama kutusuna **Geliştirici komut istemi** ' ni girin. Ardından, sonuçlar listesinden **VS 2017 için geliştirici komut istemi** seçin.

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

- [Al. exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (Tanımlayıcı Ad Aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)
- [Nasıl yapılır: Ortak özel anahtar çifti oluşturma](../../../standard/assembly/create-public-private-key-pair.md)
- [Bizimle İletişime Geçin](/visualstudio/ide/talk-to-us)
