---
title: "Nasıl yapılır: Visual Basic'de XML belgesi oluşturma"
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: d67724aad6cd3e7af30531328d85e89937390dd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551377"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de XML belgesi oluşturma
Bu örnek XML belge açıklamaları ekleme kodunuzu gösterir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>Bir tür veya üye için XML belgeleri oluşturmak için  
  
1.  İçinde **Kod Düzenleyicisi**, yukarıdaki belgeleri oluşturmak istediğiniz türe veya üyeye satırında imlecinizi.  
  
2.  Tür `'''` (üç tek tırnak işareti).  
  
     Türe veya üyeye bir XML çatısı eklenir **Kod Düzenleyicisi**.  
  
3.  Uygun etiketleri arasına tanımlayıcı bilgiler ekleyin.  
  
    > [!NOTE]
    >  XML belgeleri bloğu içinde ek satırlar eklerseniz, her bir çizgi ile başlamalıdır `'''`.  
  
4.  Türe veya üyeye yeni XML belge açıklamaları kullanan ek kod ekleyin.  
  
     IntelliSense görüntüler metinden \<Özet > türe veya üyeye etiketi.  
  
5.  Belge açıklamaları içeren bir XML dosyası oluşturmak için kodu derleyin. Daha fazla bilgi için [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XML ile Kodunuzu Belgeleme](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
