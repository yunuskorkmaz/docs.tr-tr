---
title: 'Nasıl yapılır: XML Belgesi Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 1421cc85beba42b3cf3656c34b1d02347fbaf164
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403245"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de XML Belgesi Oluşturma

Bu örnek, kodunuza XML belge açıklamaları eklemeyi gösterir.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a>Bir tür veya üye için XML belgeleri oluşturmak için

1. **Kod Düzenleyicisi**'nde imlecinizi, belge oluşturmak istediğiniz türün veya üyenin üzerindeki satıra yerleştirin.

2. Yazın `'''` (üç tek tırnak işareti).

    Tür veya üye için bir XML iskelet **kodu, kod düzenleyicisine**eklenir.

3. Uygun Etiketler arasına açıklayıcı bilgi ekleyin.

    > [!NOTE]
    > XML belge bloğunun içine ek satırlar eklerseniz, her satır ile başlamalıdır `'''` .

4. Yeni XML belge açıklamalarıyla türü veya üyeyi kullanan ek kod ekleyin.

    IntelliSense, \<summary> tür veya üyenin etiketindeki metni görüntüler.

5. Belge açıklamalarını içeren bir XML dosyası oluşturmak için kodu derleyin. Daha fazla bilgi için bkz. [-doc](../../reference/command-line-compiler/doc.md).

## <a name="see-also"></a>Ayrıca bkz.

- [XML ile Kodunuzu Belgeleme](documenting-your-code-with-xml.md)
- [XML Açıklama Etiketleri](../../language-reference/xmldoc/index.md)
- [-doc](../../reference/command-line-compiler/doc.md)
