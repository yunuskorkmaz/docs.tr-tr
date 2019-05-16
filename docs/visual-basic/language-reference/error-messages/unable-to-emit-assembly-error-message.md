---
title: 'Derleme yayılamıyor: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 012284aa42dfa29ad1a5e4ec4a4df5eaacbd4fb7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642274"
---
# <a name="unable-to-emit-assembly-error-message"></a>Derleme yayılamıyor: \<hata iletisi >

Visual Basic Derleyicisi Assembly Linker çağırır (*Al.exe*Alink olarak da bilinen) bir bildirim ve bağlayıcı sahip bir derleme oluşturmak için derleme oluşturma Emisyonu aşamasında bir hata bildirir.

**Hata Kimliği:** BC30145

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Tırnak işaretli hata iletisini inceleyin ve konusuna danışın [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) daha ayrıntılı bir açıklama ve öneriler için.

2. Derlemeyi kullanarak el ile açmayı deneyin [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) veya [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md).

3. Sorun devam ederse, koşullar hakkında bilgi toplamak ve Microsoft Ürün Destek Hizmetleri bilgilendirir.

### <a name="to-sign-the-assembly-manually"></a>Derlemeyi el ile imzalamak için

1. Kullanma [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)) bir ortak/özel anahtar çifti dosyası oluşturun.

   Bu dosyanın bir *.snk* uzantısı.

2. Projenizden hata oluşturuyor COM başvurusu silin.

3. Açık [Visual Studio için geliştirici komut istemi](../../../framework/tools/developer-command-prompt-for-vs.md).

   Windows 10, girin **Geliştirici komut istemi** görev çubuğundaki arama kutusuna. Ardından, **VS 2017 için geliştirici komut istemi** sonuçları listesinde.

4. Dizini, derleme sarmalayıcısı yerleştirmek istediğiniz dizine geçin.

5. Aşağıdaki komutu girin:

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   Şunu yazabilirsiniz gerçek komut bir örnektir:

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > Bir yol veya dosya boşluk içeriyorsa çift tırnak işaretleri kullanın.

6. Visual Studio'da oluşturduğunuz dosya bir .NET derlemesine başvuru ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (Tanımlayıcı Ad Aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)
- [Nasıl yapılır: Genel-özel anahtar çifti oluşturma](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Bizimle İletişime Geçin](/visualstudio/ide/talk-to-us)
