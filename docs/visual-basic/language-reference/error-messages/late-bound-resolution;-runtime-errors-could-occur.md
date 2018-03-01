---
title: "Sonradan bağlanma çözümlemesi; çalışma zamanı hataları oluşabilir"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d01164914b484ef689654f048a8743f3c2eb669
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>Sonradan bağlanma çözümlemesi; çalışma zamanı hataları oluşabilir
Bir nesne olması için bildirilen bir değişkene atanır [nesne veri türü](../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Bir değişken olarak bildirme zaman `Object`, derleyici gerçekleştirmelisiniz *geç bağlama*, çalışma zamanında ek işlemleri neden. Olası çalışma zamanı hataları uygulamanıza kullanıma sunar. Örneğin, eğer atarsanız bir <xref:System.Windows.Forms.Form> için `Object` değişkeni ve erişmeyi deneyin <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> özelliği, çalışma zamanı oluşturur bir <xref:System.MemberAccessException> olduğundan <xref:System.Windows.Forms.Form> sınıfı uygulamaz bir `NameTable` özelliği.  
  
 Belirli bir türde olması için değişken bildirirseniz derleyici gerçekleştirebilirsiniz *erken bağlama* derleme zamanında. Bu, Gelişmiş performans, belirli türün üyeleri ve okunabilirliği kodunuzun denetimli erişim sonuçlanır.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42017  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Mümkünse, belirli bir türde olması için değişken bildirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Erken ve geç bağlama](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [Nesne değişken bildirimi](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
