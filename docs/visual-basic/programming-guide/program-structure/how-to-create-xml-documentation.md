---
title: "Nasıl yapılır: Visual Basic'de XML Belgesi Oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 63b6485de5aba2ca49d54a057045bec2062d12dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de XML Belgesi Oluşturma
Bu örnek kodunuzu XML belge açıklamaları ekleme gösterir.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>Bir tür veya üye için XML belgeleri oluşturmak için  
  
1.  İçinde **Kod düzenleyicisinde**, imlecinizi belgeleri oluşturmak istediğiniz tür veya üye üstündeki satırın getirin.  
  
2.  Tür `'''` (üç tek tırnak işaretleri).  
  
     Tür veya üye için bir XML çatıyı eklenir **Kod düzenleyicisinde**.  
  
3.  Uygun etiketleri arasında açıklayıcı bilgileri ekleyin.  
  
    > [!NOTE]
    >  XML belgeleri bloğu içinde ek satırlar eklerseniz, her bir satır ile başlamalıdır `'''`.  
  
4.  Tür veya üye ile yeni XML belgeleri yorumları kullanan ek kodu ekleyin.  
  
     IntelliSense görüntüler metinden \<Özet > tür veya üye etiketi.  
  
5.  Belge açıklamaları içeren bir XML dosyası oluşturmak için kodu derleyin. Daha fazla bilgi için bkz: [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ile kodunuzu belgeleme](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [XML açıklama etiketleri](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [/ doc](../../../visual-basic/reference/command-line-compiler/doc.md)
