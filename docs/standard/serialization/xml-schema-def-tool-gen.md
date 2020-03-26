---
title: 'Nasıl yapılır: Sınıflar ve XML Şeması Belgeleri Oluşturmak için XML Şema Tanımı Aracını Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 4c6996e2279693cf96c826741869d72007cf81cf
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249558"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a>Nasıl yapılır: Sınıflar ve XML Şeması Belgeleri Oluşturmak için XML Şema Tanımı Aracını Kullanma
XML şema tanımı Aracı (XSD.exe'nin), bir sınıf açıklayan bir XML şeması oluşturmak veya bir XML şeması tarafından tanımlanan sınıfı oluşturmak için sağlar. Aşağıdaki yordamlar bu işlemleri gerçekleştirmek nasıl kullanılacağını göstermektedir.  
  
### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a>Belirli bir şemaya uygun sınıflar oluşturmak için  
  
1. Bir komut istemi açın.  
  
2. XML şeması için XML Şeması, örneğin tam olarak eşleştirilir sınıf kümesi oluşturur XML şema tanımı aracı için bağımsız değişken olarak geçir:  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     Araç yalnızca 16 Mart 2001 World Wide Web Consortium XML belirtimi başvuran şemaları işleyebilir. Başka bir deyişle, XML Şema adhttp://www.w3.org/2001/XMLSchemaalanı aşağıdaki örnekte gösterildiği gibi " " olmalıdır.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema" />  
    ```  
  
3. Yöntemler, özellikler veya alanları, sınıflar gerektiği şekilde değiştirin. Özniteliklerle bir sınıfı değiştirme hakkında daha fazla bilgi için bkz: [Kodlanmış SOAP Serileştirmeyi Kontrol Eden](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)Öznitelikleri ve Öznitelikleri [Kullanarak XML Serileştirmeyi Denetleme.](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
  
 Genellikle bir sınıfın (veya sınıfların) örnekleri seri hale geldiğinde oluşturulan XML akışının şemasını incelemek yararlıdır. Örneğin, şemanızı başkalarının kullanması için yayımlayabilir veya uygunluk elde etmeye çalıştığınız şema ile karşılaştırabilirsiniz.  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a>Bir XML Şeması belge sınıfları kümesinden oluşturmak için  
  
1. Sınıf veya sınıfların bir DLL içine derleyin.  
  
2. Bir komut istemi açın.  
  
3. DLL bağımsız değişken olarak XSD.exe'nin için örneğin Geçir:  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     Şema (veya şemaları) adı "schema0.xsd" ile başlayan yazılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataSet>
- [XML Şema Tanımı Aracı ve XML Serileştirme](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)
- [XML Serileştirmeye Giriş](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [XML şema tanımı Aracı (XSD.exe'nin)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Nasıl yapılır: Nesne Serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
