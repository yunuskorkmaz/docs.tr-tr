---
title: 'Nasıl yapılır: Visual Basic XML belgeleri oluşturun'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: ff93a7bb2d8fdef68fc956d4c569ca5ad37afb2c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054108"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Nasıl yapılır: Visual Basic XML belgeleri oluşturun

Bu örnek, kodunuza XML belge açıklamaları eklemeyi gösterir.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a>Bir tür veya üye için XML belgeleri oluşturmak için

1. **Kod Düzenleyicisi**'nde imlecinizi, belge oluşturmak istediğiniz türün veya üyenin üzerindeki satıra yerleştirin.

2. Yazın `'''` (üç tek tırnak işareti).

    Tür veya üye için bir XML iskelet **kodu, kod düzenleyicisine**eklenir.

3. Uygun Etiketler arasına açıklayıcı bilgi ekleyin.

    > [!NOTE]
    > XML belge bloğunun içine ek satırlar eklerseniz, her satır ile `'''`başlamalıdır.

4. Yeni XML belge açıklamalarıyla türü veya üyeyi kullanan ek kod ekleyin.

    IntelliSense, tür veya üyenin \<Özet > etiketindeki metni görüntüler.

5. Belge açıklamalarını içeren bir XML dosyası oluşturmak için kodu derleyin. Daha fazla bilgi için bkz. [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).

## <a name="see-also"></a>Ayrıca bkz.

- [XML ile Kodunuzu Belgeleme](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
