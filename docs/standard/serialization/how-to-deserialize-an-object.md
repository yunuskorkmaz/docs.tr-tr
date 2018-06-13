---
title: 'Nasıl yapılır: bir nesne seri durumdan'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: 957c332b3456e2b27aca36ef2bcabbc36b4e94e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581488"
---
# <a name="how-to-deserialize-an-object"></a>Nasıl yapılır: bir nesne seri durumdan
Bir nesne seri durumdan olduğunda aktarım biçimi akış veya dosya nesnesi oluşturacak olup olmadığını belirler. Aktarım biçimi belirlendikten sonra çağırabilirsiniz <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> veya <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> gerekli olarak yöntemler.  
  
### <a name="to-deserialize-an-object"></a>Bir nesnenin serisini kaldırmak için  
  
1.  Oluşturmak bir <xref:System.Xml.Serialization.XmlSerializer> seri durumdan çıkarılacak nesne türünü kullanarak.  
  
2.  Arama <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> nesnenin bir kopyasını oluşturmak için yöntemi. Seri durumdan çıkarılırken, özgün türü döndürülen nesneyi (Bu da bir akışa seri durumdan çıkarılamadı rağmen), bir dosyaya nesne seri durumdan çıkarır aşağıdaki örnekte gösterildiği gibi dönüştürmeniz gerekir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Serileştirmeye Giriş](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [Nasıl yapılır: Nesne Serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object.md)
