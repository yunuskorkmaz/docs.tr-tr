---
title: "'<assemblyidentity>' türünü içeren '<typename>' derlemesi için başvuru gerekiyordu, ancak '<projectname1>' ile '<projectname2>' projeleri arasındaki belirsizlik nedeniyle uygun bir başvuru bulunamadı"
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 9868598b32ae17ef5bfb5dd738f8a7541515f5ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013757"
---
# <a name="reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a>Derlemesine başvuru gereklidir '\<assemblyIdentity >' türünü içeren '\<typename >', ancak proje arasındaki belirsizlik nedeniyle uygun bir başvuru bulunamadı\<projectname1 >' ve '\< projectname2 >'
Sınıfı, yapıyı, arabirimi, sabit listesi veya projenizin dışında tanımlı temsilci, gibi bir tür bir ifade kullanır. Ancak, birden fazla derleme türü tanımlayan proje başvurularına sahip.  
  
 Alıntı projeleri, aynı ada sahip derlemeler üretir. Bu nedenle, derleyici tür için kullanmak üzere hangi derleme erişme belirlenemiyor.  
  
 Başka bir derlemede tanımlanan bir türü erişmek için Visual Basic Derleyicisi derlemeye bir başvuru olmalıdır. Bu projeler arasında döngüsel başvurulara neden olmaz tek ve eksiksiz bir başvuru olmalıdır.  
  
 **Hata Kimliği:** BC30969  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Başvurmak için en iyi derleme projeniz için proje üretir belirleyin. Bu kararı, dosya erişim kolaylığı ve güncelleştirmelerinin sıklığı gibi ölçütlere kullanabilir.  
  
2. Proje özelliklerinizi kullanmakta olduğunuz türü tanımlayan bir derlemeyi içeren dosyaya bir başvuru ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
- [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [Bozuk Başvurularda Sorun Giderme](/visualstudio/ide/troubleshooting-broken-references)
