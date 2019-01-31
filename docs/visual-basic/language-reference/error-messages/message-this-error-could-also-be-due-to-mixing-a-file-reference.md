---
title: <message> Bu hataya bir dosya başvurusu ile '<assemblyname>' derlemesine yapılan proje başvurusunun karışması da neden olmuş olabilir
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: f28327b4df5b15f368f736e7402179227035a06e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272558"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a>\<İleti > Bu hata, bir dosya başvurusu ile derleme yapılan proje başvurusunun karışması da olabilir '\<assemblyname >'
\<İleti > Bu hata, bir dosya başvurusu ile derleme yapılan proje başvurusunun karışması da olabilir '\<assemblyname >. Bu durumda, dosya başvurusu değiştirmeyi deneyin. '\<assemblyfilename >' projesindeki '\<projectname1 >' proje başvurusu ile '\<projectname2 >'.  
  
 Kodu, projenizdeki başka bir proje üyesi erişen ancak çözümünüz yapılandırmasını başvuru çözmek Visual Basic Derleyicisi izin vermiyor.  
  
 Başka bir derlemede tanımlanan bir türü erişmek için Visual Basic Derleyicisi derlemeye bir başvuru olmalıdır. Bu projeler arasında döngüsel başvurulara neden olmaz tek ve eksiksiz bir başvuru olmalıdır.  
  
 **Hata Kimliği:** BC30971  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Başvurmak için en iyi derleme projeniz için proje üretir belirleyin. Bu kararı, dosya erişim kolaylığı ve güncelleştirmelerinin sıklığı gibi ölçütlere kullanabilir.  
  
2.  Proje özelliklerinizi kullanmakta olduğunuz türü tanımlayan derleme içeren projeye başvuru ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
- [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [Bozuk Başvurularda Sorun Giderme](/visualstudio/ide/troubleshooting-broken-references)
