---
title: Otomatik (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1e32c4c910567829a4f5c59b48020db4dfbbeb7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="auto-visual-basic"></a>Otomatik (Visual Basic)
Visual Basic dizeleri bildirilen dış yordamı dış adını temel alarak .NET Framework kurallarına göre sıralama belirtir.  
  
 Projenizin dışında tanımlı bir yordam çağrısı, Visual Basic derleyici doğru yordam çağrısı için gereken bilgilere erişimi yok. Bu bilgiler yordamı bulunduğu, nasıl tanımlanır, kendi arama sırası ve dönüş türü içerir ve dize karakter kullanır ayarlayın. [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md) dış bir yordam için bir başvuru oluşturur ve bu gerekli bilgileri sağlar.  
  
 `charsetmodifier` Bölümün `Declare` deyimi dış yordamı yapılan bir çağrı sırasında dizeleri sıralama için karakter kümesi bilgileri sağlar. Visual Basic dış yordamı adı için dış dosyasını nasıl arayacağını etkiler. `Auto` Değiştiricisi belirtir Visual Basic .NET Framework kurallarına göre dizeleri sıralama ve gerekir temel karakter çalışma zamanı platform ve muhtemelen kümesini belirlemelisiniz ilk arıyorsanız dış yordam adı değiştirin, başarısız olur. Daha fazla bilgi için bkz: "Karakter kümesi" [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md).  
  
 Herhangi bir karakter kümesi değiştiricisi belirtilirse, `Ansi` varsayılandır.  
  
## <a name="remarks"></a>Açıklamalar  
 `Auto` Bu bağlamda değiştirici kullanılabilir:  
  
 [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  
 Bu anahtar sözcük desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [Anahtar sözcükler](../../../visual-basic/language-reference/keywords/index.md)
