---
title: "&lt;İleti&gt; bu hata, ayrıca bir proje başvurusu derleme &#39; dosya başvurusuyla karıştırılması nedeniyle olabilir&lt; AssemblyName&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords: BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0fcbcc48928b1b03487f31930e3d14051ddd990a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a>&lt;İleti&gt; bu hata, ayrıca bir proje başvurusu derleme &#39; dosya başvurusuyla karıştırılması nedeniyle olabilir&lt; AssemblyName&gt;&#39;
\<İleti > Bu hata, ayrıca bir proje başvurusu derleme dosyası başvurusuyla karıştırılması nedeniyle olabilir '\<assemblyname >. Bu durumda, dosya başvurusunu değiştirmeyi deneyin '\<assemblyfilename >' projesindeki '\<projectname1 >' proje başvuru '\<projectname2 >'.  
  
 Projenizdeki kod erişen başka bir projeye üyesi ancak çözümünüz yapılandırılmasına izin vermez [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici başvurusu çözümlenemiyor.  
  
 Başka bir derlemede tanımlanan bir türü erişmek için [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici, bu derleme başvurusu olmalıdır. Bu, projeler arasında döngüsel başvuru neden olmaz tek ve anlaşılır bir başvurusu olmalıdır.  
  
 **Hata Kimliği:** BC30971  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Başvurmak için en iyi derleme projeniz için hangi proje üreten belirler. Bu karar, dosya erişim kolaylığı ve güncelleştirme sıklığını gibi ölçütlere kullanabilir.  
  
2.  Proje Özellikleri'nde, kullanmakta olduğunuz türü tanımlayan derleme içeren projesine bir başvuru ekleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)  
 [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)  
 [Bozuk Başvurularda Sorun Giderme](/visualstudio/ide/troubleshooting-broken-references)
