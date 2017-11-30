---
title: "Derleme &#39;için gereken başvuru; &lt;assemblyIdentity&gt;&#39; içeren türü &#39;&lt; TypeName&gt;&#39; ancak uygun bir başvuru projeleri &#39; arasındaki belirsizlik nedeniyle bulunamadı&lt; projectname1&gt;&#39; ve &#39;&lt; projectname2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords: BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 04a1b16a10d2a3945d1efbe3a2bd0850f1da39fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a>Derleme &#39;için gereken başvuru; &lt;assemblyIdentity&gt;&#39; içeren türü &#39;&lt; TypeName&gt;&#39; ancak uygun bir başvuru projeleri &#39; arasındaki belirsizlik nedeniyle bulunamadı&lt; projectname1&gt;&#39; ve &#39;&lt; projectname2&gt;&#39;
Sınıfı, yapısı, arabirim, numaralandırma veya projenizin dışında tanımlı temsilci, gibi bir tür bir ifade kullanır. Ancak, birden fazla derleme bu türünü tanımlamak için proje başvuruları sahip.  
  
 Alıntı projeleri aynı ada sahip derlemeler üretir. Bu nedenle, derleyicinin türü için kullanmak üzere hangi derleme erişme belirleyemiyor.  
  
 Başka bir derlemede tanımlanan bir türü erişmek için [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici, bu derleme başvurusu olmalıdır. Bu, projeler arasında döngüsel başvuru neden olmaz tek ve anlaşılır bir başvurusu olmalıdır.  
  
 **Hata Kimliği:** BC30969  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Başvurmak için en iyi derleme projeniz için hangi proje üreten belirler. Bu karar, dosya erişim kolaylığı ve güncelleştirme sıklığını gibi ölçütlere kullanabilir.  
  
2.  Proje Özellikleri'nde, kullanmakta olduğunuz türü tanımlayan derleme içeren dosyaya bir başvuru ekleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)  
 [Bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [NIB nasıl yapılır: başvuru ekleme veya kaldırma Başvuru Ekle iletişim kutusunu kullanarak](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)  
 [Bozuk başvurularda sorun giderme](/visualstudio/ide/troubleshooting-broken-references)
