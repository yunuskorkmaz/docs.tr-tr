---
title: 'Nasıl yapılır: Sınıflar ve XML Şeması Belgeleri Oluşturmak için XML Şema Tanımı Aracını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 77bb567d2b7b8fff2b1b8de43b2d5fa36fffb3b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62017988"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a>Nasıl yapılır: Sınıflar ve XML Şeması Belgeleri Oluşturmak için XML Şema Tanımı Aracını Kullanma
XML şema tanımı Aracı (XSD.exe'nin), bir sınıf açıklayan bir XML şeması oluşturmak veya bir XML şeması tarafından tanımlanan sınıfı oluşturmak için sağlar. Aşağıdaki yordamlar bu işlemleri gerçekleştirmek nasıl kullanılacağını göstermektedir.  
  
### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a>Belirli bir şemaya uygun sınıflar oluşturmak için  
  
1. Bir komut istemi açın.  
  
2. XML şeması için XML Şeması, örneğin tam olarak eşleştirilir sınıf kümesi oluşturur XML şema tanımı aracı için bağımsız değişken olarak geçir:  
  
    ```  
    xsd mySchema.xsd  
    ```  
  
     Araç yalnızca 16 Mart 2001 World Wide Web Consortium XML belirtimi başvuran şemaları işleyebilir. Diğer bir deyişle, XML Şema ad olmalıdır "http://www.w3.org/2001/XMLSchema" aşağıdaki örnekte gösterildiği gibi.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    ```  
  
3. Yöntemler, özellikler veya alanları, sınıflar gerektiği şekilde değiştirin. Sınıfı öznitelikler değiştirme hakkında daha fazla bilgi için bkz. [XML serileştirme kullanarak özniteliklerini denetleme](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) ve [öznitelikleri emin denetim kodlanmış SOAP serileştirme](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
 Genellikle, bir sınıf (veya sınıfları) örneklerini serileştirildiği zaman oluşturan XML akışının şeması incelemek kullanışlıdır. Örneğin, şemanızı kullanmak üzere başkalarını için yayımlama veya uyumluluğu elde etmek çalıştığınız bir şemaya karşılaştırma.  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a>Bir XML Şeması belge sınıfları kümesinden oluşturmak için  
  
1. Sınıf veya sınıfların bir DLL içine derleyin.  
  
2. Bir komut istemi açın.  
  
3. DLL bağımsız değişken olarak XSD.exe'nin için örneğin Geçir:  
  
    ```  
    xsd MyFile.dll  
    ```  
  
     Şema (veya şemaları) adı "schema0.xsd" ile başlayan yazılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataSet>
- [XML Şema Tanımı Aracı ve XML Serileştirme](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)
- [XML Serileştirmeye Giriş](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [XML Şema Tanımı Aracı (XSD.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Nasıl yapılır: Bir nesneyi serileştirmek](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [Nasıl yapılır: Bir nesneyi seri durumdan çıkarma](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
