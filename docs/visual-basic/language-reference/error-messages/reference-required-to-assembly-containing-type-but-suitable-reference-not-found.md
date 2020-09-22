---
title: "'<assemblyidentity>' türünü içeren '<typename>' derlemesi için başvuru gerekiyordu, ancak '<projectname1>' ile '<projectname2>' projeleri arasındaki belirsizlik nedeniyle uygun bir başvuru bulunamadı"
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: ffc6b3c180c86abe272d56d0ecf3042d8181da59
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870894"
---
# <a name="reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a>'\<assemblyidentity>' türünü içeren '\<typename>' derlemesi için başvuru gerekiyordu, ancak '\<projectname1>' ile '\<projectname2>' projeleri arasındaki belirsizlik nedeniyle uygun bir başvuru bulunamadı

Bir ifade, projenizin dışında tanımlanan bir sınıf, yapı, arabirim, numaralandırma veya temsilci gibi bir tür kullanır. Ancak, bu türü tanımlayan birden fazla derlemeye proje başvuruları vardır.  
  
 Alıntı yapılan projeler aynı ada sahip derlemeler üretir. Bu nedenle, derleyici eriştiğiniz tür için hangi derlemeyi kullanacağınızı belirleyemez.  
  
 Başka bir derlemede tanımlı bir türe erişmek için, Visual Basic derleyicisinin bu derlemeye bir başvurusu olmalıdır. Bu, projeler arasında döngüsel başvurulara neden olmayan tek, belirsiz bir başvuru olmalıdır.  
  
 **Hata kimliği:** BC30969  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Projenizin başvurması için en iyi derlemeyi hangi projenin ürettiğini belirleme. Bu karar için dosya erişiminin ve güncelleştirme sıklığının kolaylığı gibi ölçütleri kullanabilirsiniz.  
  
2. Proje özelliklerinde, kullanmakta olduğunuz türü tanımlayan derlemeyi içeren dosyaya bir başvuru ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
- [Bildirilmiş Öğelere Başvurular](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [Bozuk Başvurularda Sorun Giderme](/visualstudio/ide/troubleshooting-broken-references)
