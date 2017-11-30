---
title: "While Serializing3 boşluk koruma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: df0ee9bedd4123ac47c06d1c64f305fcf0b0825a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="preserving-white-space-while-serializing"></a>Beyaz alan Serileştirirken koruma
Bu konuda, bir XML ağacı serileştirilirken boşluk denetlemek açıklar.  
  
 Girintili XML okuma, bir bellek içi XML ağacı boşluk metin düğüm (diğer bir deyişle, değil koruma boşluk) olmadan oluşturmak, XML bazı işlemleri ve ardından XML girintileme ile kaydetmek için yaygın bir senaryo değil. Biçimlendirmeye sahip XML serileştirme, yalnızca önemli boşluk XML ağacında korunur. Varsayılan davranışı budur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Okumak ve özellikle girintili zaten XML değiştirmek için başka bir yaygın bir senaryo değil. Bu girinti herhangi bir şekilde değiştirmek istemeyebilirsiniz. Bunu yapmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], yükleme veya XML Ayrıştırma ve XML serileştirme zaman biçimlendirme devre dışı olduğunda boşluk korumak.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>Beyaz alan davranışı XML ağaçları Serialize yöntemi  
 Aşağıdaki yöntemleri <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> sınıfları seri bir XML ağacı. Bir dosyayı bir XML ağaca serileştirebiliyorsa bir <xref:System.IO.TextReader>, veya bir <xref:System.Xml.XmlReader>. `ToString` Yöntemi serileştiren bir dize.  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 Yöntem değil izlerseniz <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak, ardından yöntemi biçimlendirir (Girinti) serileştirilmiş XML. Bu durumda, tüm anlamsız boşluk XML ağacında göz ardı edilir.  
  
 Yöntem izlerseniz <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak, ardından yöntemi biçimlendirme olduğunu belirleyebilirsiniz (Girinti) serileştirilmiş XML. Bu durumda, tüm boşluk XML ağacında korunur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Biçimlendiricisi XML ağaçları (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
