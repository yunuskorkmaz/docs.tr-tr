---
title: "Nasıl yapılır: sınıfları ve XML Şeması belgeleri oluşturmak üzere XML şema tanımı aracını kullanın"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c1f0dd08e820e5433f05c8bc90d85c84eb05972
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a>Nasıl yapılır: sınıfları ve XML Şeması belgeleri oluşturmak üzere XML şema tanımı aracını kullanın
XML şema tanımı Aracı (XSD.exe'nin), bir sınıf açıklayan bir XML şeması oluşturmak veya bir XML şeması tarafından tanımlanan sınıfı oluşturmak için sağlar. Aşağıdaki yordamlar bu işlemleri gerçekleştirmek nasıl kullanılacağını göstermektedir.  
  
### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a>Belirli bir şemaya uygun sınıflar oluşturmak için  
  
1.  Bir komut istemi açın.  
  
2.  XML şeması için XML Şeması, örneğin tam olarak eşleştirilir sınıf kümesi oluşturur XML şema tanımı aracı için bağımsız değişken olarak geçir:  
  
    ```  
    xsd mySchema.xsd  
    ```  
  
     Araç yalnızca 16 Mart 2001 World Wide Web Consortium XML belirtimi başvuran şemaları işleyebilir. Diğer bir deyişle, XML Şema ad alanı aşağıdaki örnekte gösterildiği gibi "http://www.w3.org/2001/XMLSchema" olmalıdır.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    ```  
  
3.  Yöntemler, özellikler veya alanları, sınıflar gerektiği şekilde değiştirin. Sınıf öznitelikleri ile değiştirme hakkında daha fazla bilgi için bkz: [XML serileştirme kullanarak özniteliklerini denetleme](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) ve [öznitelikleri, Denetim kodlanmış SOAP seri hale getirme](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
 Genellikle, bir sınıf (veya sınıfları) örneklerini serileştirildiği zaman oluşturan XML akışı şeması incelemek kullanışlıdır. Örneğin, başkalarının kullanmak şemanızı yayımlayabilir veya uygunluk elde etmek çalıştığınız bir şemaya karşılaştırmak.  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a>Bir XML Şeması belge sınıfları kümesinden oluşturmak için  
  
1.  Sınıf veya sınıfların bir DLL içine derleyin.  
  
2.  Bir komut istemi açın.  
  
3.  DLL bağımsız değişken olarak XSD.exe'nin için örneğin Geçir:  
  
    ```  
    xsd MyFile.dll  
    ```  
  
     Şema (veya şemaları) adı "schema0.xsd" ile başlayan yazılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataSet>  
 [XML şema tanımı aracı ve XML serileştirme](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 [Giriş XML serileştirme](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [XML şema tanımı aracını (XSD.exe'nin)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Nasıl yapılır: bir nesneyi serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Nasıl yapılır: bir nesne seri durumdan](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
