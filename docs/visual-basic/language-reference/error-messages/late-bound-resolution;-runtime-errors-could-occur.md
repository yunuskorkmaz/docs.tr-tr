---
title: Sonradan bağlanma çözümlemesi; çalışma zamanı hataları oluşabilir
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 1c7b352c7bd61216ecce9901585945e740428ee3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873861"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>Sonradan bağlanma çözümlemesi; çalışma zamanı hataları oluşabilir

Nesne [veri türü](../data-types/object-data-type.md)olarak belirtilen bir değişkene bir nesne atanır.  
  
 Olarak bir değişken bildirdiğinizde `Object` , derleyicinin *geç bağlama*gerçekleştirmesi gerekir ve bu, çalışma zamanında ek işlemlere neden olur. Ayrıca, uygulamanızı olası çalışma zamanı hatalarına da sunar. Örneğin, değişkenine bir atar <xref:System.Windows.Forms.Form> `Object` ve sonra özelliğe erişmeyi denerseniz <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> , <xref:System.MemberAccessException> sınıf bir <xref:System.Windows.Forms.Form> özelliği kullanıma sunmadığından çalışma zamanı bir oluşturur `NameTable` .  
  
 Değişkeni belirli bir türde olacak şekilde bildirirseniz, derleyici derleme zamanında *erken bağlama* gerçekleştirebilir. Bu, belirli türde üyelere gelişmiş performans, denetimli erişim ve kodunuzun daha iyi okunmasına neden olur.  
  
 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata kimliği:** BC42017  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Mümkünse, değişkeni belirli bir türde olacak şekilde bildirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Erken ve geç bağlama](../../programming-guide/language-features/early-late-binding/index.md)
- [Nesne Değişken Bildirimi](../../programming-guide/language-features/variables/object-variable-declaration.md)
