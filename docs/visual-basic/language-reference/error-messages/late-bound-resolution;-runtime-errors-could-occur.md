---
title: Sonradan bağlanma çözümlemesi; çalışma zamanı hataları oluşabilir
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 6b78dfed1d615ba865f136365eac1c9c131ed5a5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661942"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>Sonradan bağlanma çözümlemesi; çalışma zamanı hataları oluşabilir
Bir nesne olması için bildirilen bir değişkene atanır [nesne veri türü](../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Olarak bir değişken bildirdiğinizde `Object`, derleyici gerçekleştirmelidir *geç bağlama*, çalışma zamanında ek işlemler sağlar. Olası çalışma zamanı hataları uygulamanızı kullanıma sunar. Örneğin, atadığınız bir <xref:System.Windows.Forms.Form> için `Object` değişkeni ve erişmeyi deneyin <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> özelliği, çalışma zamanı oluşturur bir <xref:System.MemberAccessException> çünkü <xref:System.Windows.Forms.Form> sınıfı koymuyor bir `NameTable` özelliği.  
  
 Belirli bir türde olması için değişken bildirirseniz derleyici gerçekleştirebilirsiniz *erken bağlama* derleme zamanında. Bu, Gelişmiş performans, belirli bir türün üyeleri ve kodunuzun okunabilirliği denetimli erişim sonuçlanır.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42017  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Mümkünse, belirli bir türde olması değişkeni bildirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Erken ve Geç Bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [Nesne Değişken Bildirimi](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
