---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic XML belgeleri oluşturma'
title: 'Nasıl yapılır: XML Belgesi Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: d54c79d820a170b246e5c85d7562487fbe66f39c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475961"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de XML Belgesi Oluşturma

Bu örnek, kodunuza XML belge açıklamaları eklemeyi gösterir.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a>Bir tür veya üye için XML belgeleri oluşturmak için

1. **Kod Düzenleyicisi**'nde imlecinizi, belge oluşturmak istediğiniz türün veya üyenin üzerindeki satıra yerleştirin.

2. Yazın `'''` (üç tek tırnak işareti).

    Tür veya üye için bir XML iskelet **kodu, kod düzenleyicisine** eklenir.

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
