---
title: Derlemesine başvuru gereklidir &#39; &lt;assemblyIdentity&gt; &#39; türünü içeren &#39; &lt;typename&gt;&#39;, ancak arasındaki belirsizlik nedeniyle uygun bir başvuru bulunamadı projeleri &#39; &lt;projectname1&gt; &#39; ve &#39; &lt;projectname2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 1a0c2a2fd235026729901153a0c0c300f914a78f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553015"
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a>Derlemesine başvuru gereklidir &#39; &lt;assemblyIdentity&gt; &#39; türünü içeren &#39; &lt;typename&gt;&#39;, ancak arasındaki belirsizlik nedeniyle uygun bir başvuru bulunamadı projeleri &#39; &lt;projectname1&gt; &#39; ve &#39; &lt;projectname2&gt;&#39;
Sınıfı, yapıyı, arabirimi, sabit listesi veya projenizin dışında tanımlı temsilci, gibi bir tür bir ifade kullanır. Ancak, birden fazla derleme türü tanımlayan proje başvurularına sahip.  
  
 Alıntı projeleri, aynı ada sahip derlemeler üretir. Bu nedenle, derleyici tür için kullanmak üzere hangi derleme erişme belirlenemiyor.  
  
 Başka bir derlemede tanımlanan bir türü erişmek için Visual Basic Derleyicisi derlemeye bir başvuru olmalıdır. Bu projeler arasında döngüsel başvurulara neden olmaz tek ve eksiksiz bir başvuru olmalıdır.  
  
 **Hata Kimliği:** BC30969  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Başvurmak için en iyi derleme projeniz için proje üretir belirleyin. Bu kararı, dosya erişim kolaylığı ve güncelleştirmelerinin sıklığı gibi ölçütlere kullanabilir.  
  
2.  Proje özelliklerinizi kullanmakta olduğunuz türü tanımlayan bir derlemeyi içeren dosyaya bir başvuru ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
- [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [Bozuk Başvurularda Sorun Giderme](/visualstudio/ide/troubleshooting-broken-references)
