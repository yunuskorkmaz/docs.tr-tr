---
title: "Bir Numaralandırmanın Ne Zaman Kullanılacağı (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3b2937cc71c0c31bd8dce3d77fb33f48e1b5750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Bir Numaralandırmanın Ne Zaman Kullanılacağı (Visual Basic)
Numaralandırmalar ilgili sabitleri kümeleriyle çalışmak için kolay bir yol sunar. Numaralandırma, bir ya da `Enum`, değer kümesi için bir simgesel ad. Numaralandırmalar veri türleri olarak kabul edilir ve değişkenleri ve özellikleri ile kullanım için sabitleri kümesi oluşturmak için kullanabilirsiniz.  
  
## <a name="when-to-use-an-enumeration"></a>Bir Numaralandırmanın Ne Zaman Kullanılacağı  
 Her bir yordam sınırlı sayıda değişkenleri kabul eder, numaralandırma kullanmayı düşünün. Özellikle anlamlı adları kullanıldığında numaralandırmalar NET ve daha okunabilir kodunu olun.  
  
 Numaralandırmalar kullanmanın avantajları şunlardır:  
  
-   Sırasını değiştirme veya numaraları yanlış yazmanız kaynaklanan hataları azaltır.  
  
-   Gelecekte değerlerini değiştirmek kolaylaştırır.  
  
-   Hataları içine şekilde işi olasılığını anlamına gelen kod okumak daha kolay hale getirir.  
  
-   İleriye dönük uyumluluk sağlar. Numaralandırmalar ile kodunuzu gelecekte birinin üyesi adlarına karşılık gelen değerleri değişirse başarısız daha az olasıdır.  
  
## <a name="naming-enumerations"></a>Numaralandırmalar adlandırma  
 Numaralandırma üyeleri için bir adlandırma kuralını kullanın. Zaman [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bir numaralandırma üye adı karşılaştığında diğer başvurulan tür kitaplıklarının aynı ada sahip olması durumunda bir özel durum oluşturulabilir. Uygulama veya bileşenin değerleri tanımlayan benzersiz bir ön ekini kullanın.  
  
 Bir numaralandırma üyesi için söz konusu olduğunda, numaralandırma adıyla üye nitelemek veya desteklemeli kullanmak `Imports` deyimi. Daha fazla bilgi için bkz: [numaralandırmalar ve ad niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Önceden tanımlanmış numaralandırmaları  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]önceden tanımlanmış numaralandırmalar sayısı gibi sağlar `FirstDayOfWeek` ve `MsgBoxResult`, kodunuzu kolaylaştırmak için. Bunların listesi için bkz: [sabitler ve numaralandırmalar](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Nasıl yapılır: bir numaralandırma üyesine başvurma](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Numaralandırmalar ve ad niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Nasıl yapılır: Visual Basic'de numaralandırma yoluyla yineleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Nasıl yapılır: bir numaralandırma değeriyle ilişkili dizeyi belirleme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Enum deyimi](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Sabitler ve numaralandırmalar](../../../../visual-basic/language-reference/constants-and-enumerations.md)
