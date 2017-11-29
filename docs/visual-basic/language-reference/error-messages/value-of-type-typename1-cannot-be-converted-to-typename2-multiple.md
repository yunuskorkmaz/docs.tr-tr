---
title: "Değer türü &#39; &lt;typename1&gt;&#39; dönüştürülemiyor &#39;&lt; TypeName2&gt;&#39; (Birden çok dosya başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords: BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cc6138c7a7ca7d50a56fdd1f536e8d2dc3462a08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>Değer türü &#39; &lt;typename1&gt;&#39; dönüştürülemiyor &#39;&lt; TypeName2&gt;&#39; (Birden çok dosya başvurusu)
Türündeki değeri '\<typename1 >' şekilde dönüştürülemeyen '\<typename2 >'. Tür uyuşmazlığı dosya başvurusu karıştırma nedeniyle olabilir '\<filepath1 >' projesindeki '\<projectname1 >' dosya başvuru '\<filepath2 >' projesindeki '\<projectname2 >'. Her iki derlemeleri özdeş ise, her iki başvuruları aynı konumdan; bu nedenle bu başvuruları değiştirmeyi deneyin.  
  
 Burada bir proje derleme birden fazla dosya başvuru yapar bir durumda, bir tür için başka bir dönüştürülebileceğinden derleyici garanti edemez.  
  
 Her dosya başvurusu, bir dosya yolu ve bir proje (genellikle bir DLL dosyası) çıkış dosyasının adı belirtir. Derleyici çıktı dosyaları aynı kaynaktan geldiği ya da aynı bütünleştirilmiş kodda aynı sürümünü temsil ettiğini garanti edemez. Bu nedenle, onu farklı başvuru türlerinde aynı türde olan veya hatta bir diğerine dönüştürülebilir garanti edemez.  
  
 Başvurulan derlemeler aynı derleme kimliğine sahip olduğunu biliyorsanız, tek bir dosya başvuru kullanabilirsiniz. *Derleme kimliği* derlemenin adı, sürüm, ortak anahtar varsa ve kültür içerir. Bu bilgiler, derleme benzersiz olarak tanımlar.  
  
 **Hata Kimliği:** BC30961  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Başvurulan derlemeler aynı derleme kimliğine varsa, kaldırın veya yalnızca tek bir dosya başvuru olmasını sağlamak başvurulara birini değiştirin.  
  
-   Başvurulan derlemeler aynı derleme kimliğine yoksa türü bir diğer türüne dönüştürmek denemez şekilde ardından kodunuzu değiştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de tür dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)  
 [NIB nasıl yapılır: başvuru ekleme veya kaldırma Başvuru Ekle iletişim kutusunu kullanarak](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
