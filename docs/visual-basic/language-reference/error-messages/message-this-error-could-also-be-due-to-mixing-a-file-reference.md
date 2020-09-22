---
title: <message> Bu hataya bir dosya başvurusu ile '<assemblyname>' derlemesine yapılan proje başvurusunun karışması da neden olmuş olabilir
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: cd2c00bda5b63abbd6bf7069ef28d0a812b22044
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873782"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a>\<message> Bu hataya bir dosya başvurusu ile '\<assemblyname>' derlemesine yapılan proje başvurusunun karışması da neden olmuş olabilir

\<message> Bu hata, bir dosya başvurusunu derleme ' a bir proje başvurusuyla karıştırmaya neden olmuş olabilir \<assemblyname> . Bu durumda, ' ' projesindeki ' ' adlı dosya başvurusunu ' ' \<assemblyfilename> \<projectname1> için bir proje başvurusuyla değiştirmeyi deneyin \<projectname2> .  
  
 Projenizdeki kod başka bir projenin üyesine erişir, ancak çözümünüzün yapılandırması, Visual Basic derleyicisinin başvuruyu çözümlemesine izin vermez.  
  
 Başka bir derlemede tanımlı bir türe erişmek için, Visual Basic derleyicisinin bu derlemeye bir başvurusu olmalıdır. Bu, projeler arasında döngüsel başvurulara neden olmayan tek, belirsiz bir başvuru olmalıdır.  
  
 **Hata kimliği:** BC30971  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Projenizin başvurması için en iyi derlemeyi hangi projenin ürettiğini belirleme. Bu karar için dosya erişiminin ve güncelleştirme sıklığının kolaylığı gibi ölçütleri kullanabilirsiniz.  
  
2. Proje özelliklerinde, kullanmakta olduğunuz türü tanımlayan derlemeyi içeren projeye bir başvuru ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
- [Bildirilmiş Öğelere Başvurular](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [Bozuk Başvurularda Sorun Giderme](/visualstudio/ide/troubleshooting-broken-references)
