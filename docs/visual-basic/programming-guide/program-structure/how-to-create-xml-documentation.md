---
title: 'Nasıl yapılır: XML Belgesi Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 41b7ef1f435fd0a4f20c4ca2936e2d91e155f7c5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347418"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de XML Belgesi Oluşturma

Bu örnek, kodunuza XML belge açıklamaları eklemeyi gösterir.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a>Bir tür veya üye için XML belgeleri oluşturmak için

1. **Kod Düzenleyicisi**'nde imlecinizi, belge oluşturmak istediğiniz türün veya üyenin üzerindeki satıra yerleştirin.

2. `'''` yazın (üç tek tırnak işareti).

    Tür veya üye için bir XML iskelet **kodu, kod düzenleyicisine**eklenir.

3. Uygun Etiketler arasına açıklayıcı bilgi ekleyin.

    > [!NOTE]
    > XML belge bloğunun içine ek satırlar eklerseniz, her satır `'''`başlamalıdır.

4. Yeni XML belge açıklamalarıyla türü veya üyeyi kullanan ek kod ekleyin.

    IntelliSense, tür veya üye için \<Özet > etiketindeki metni görüntüler.

5. Belge açıklamalarını içeren bir XML dosyası oluşturmak için kodu derleyin. Daha fazla bilgi için bkz. [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).

## <a name="see-also"></a>Ayrıca bkz.

- [XML ile Kodunuzu Belgeleme](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)
