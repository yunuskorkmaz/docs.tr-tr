---
title: 'Nasıl yapılır: Bir nesneyi seri durumdan çıkarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: d0b953e4f570f349edeb80fc2316530494905ec0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583317"
---
# <a name="how-to-deserialize-an-object"></a>Nasıl yapılır: Bir nesneyi seri durumdan çıkarma
Bir nesnenin serisini olduğunda, taşıma biçimi bir akış veya dosya nesnesi oluşturacak olup olmadığını belirler. Taşıma biçimi belirlendikten sonra çağırabilirsiniz <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> veya <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> , gerekli olarak yöntemler.  
  
### <a name="to-deserialize-an-object"></a>Bir nesnenin serisini kaldırmak için  
  
1.  Oluşturmak bir <xref:System.Xml.Serialization.XmlSerializer> seri durumdan çıkarılacak nesne türü kullanarak.  
  
2.  Arama <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> nesnenin bir kopyasını oluşturmak için yöntemi. Seri durumdan çıkarmak olduğunda döndürülen nesne özgün türü (Bu aynı zamanda bir akışa seri durumdan olsa da) bir dosyaya nesne seri durumdan çıkarır aşağıdaki örnekte gösterildiği gibi dönüştürmeniz gerekir.  
  
    ```vb  
    Dim myObject As MySerializableClass  
    ' Construct an instance of the XmlSerializer with the type  
    ' of object that is being deserialized.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To read the file, create a FileStream.  
    Dim myFileStream As FileStream = _  
    New FileStream("myFileName.xml", FileMode.Open)  
    ' Call the Deserialize method and cast to the object type.  
    myObject = CType( _  
    mySerializer.Deserialize(myFileStream), MySerializableClass)  
    ```  
  
    ```csharp  
    MySerializableClass myObject;  
    // Construct an instance of the XmlSerializer with the type  
    // of object that is being deserialized.  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(MySerializableClass));  
    // To read the file, create a FileStream.  
    FileStream myFileStream =   
    new FileStream("myFileName.xml", FileMode.Open);  
    // Call the Deserialize method and cast to the object type.  
    myObject = (MySerializableClass)   
    mySerializer.Deserialize(myFileStream)  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Serileştirmeye Giriş](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [Nasıl yapılır: Bir nesneyi serileştirmek](../../../docs/standard/serialization/how-to-serialize-an-object.md)
