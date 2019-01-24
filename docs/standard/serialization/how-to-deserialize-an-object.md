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
# <a name="how-to-deserialize-an-object"></a><span data-ttu-id="05228-102">Nasıl yapılır: Bir nesneyi seri durumdan çıkarma</span><span class="sxs-lookup"><span data-stu-id="05228-102">How to: Deserialize an Object</span></span>
<span data-ttu-id="05228-103">Bir nesnenin serisini olduğunda, taşıma biçimi bir akış veya dosya nesnesi oluşturacak olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="05228-103">When you deserialize an object, the transport format determines whether you will create a stream or file object.</span></span> <span data-ttu-id="05228-104">Taşıma biçimi belirlendikten sonra çağırabilirsiniz <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> veya <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> , gerekli olarak yöntemler.</span><span class="sxs-lookup"><span data-stu-id="05228-104">After the transport format is determined, you can call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> or <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> methods, as required.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="05228-105">Bir nesnenin serisini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="05228-105">To deserialize an object</span></span>  
  
1.  <span data-ttu-id="05228-106">Oluşturmak bir <xref:System.Xml.Serialization.XmlSerializer> seri durumdan çıkarılacak nesne türü kullanarak.</span><span class="sxs-lookup"><span data-stu-id="05228-106">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object to deserialize.</span></span>  
  
2.  <span data-ttu-id="05228-107">Arama <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> nesnenin bir kopyasını oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="05228-107">Call the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> method to produce a replica of the object.</span></span> <span data-ttu-id="05228-108">Seri durumdan çıkarmak olduğunda döndürülen nesne özgün türü (Bu aynı zamanda bir akışa seri durumdan olsa da) bir dosyaya nesne seri durumdan çıkarır aşağıdaki örnekte gösterildiği gibi dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="05228-108">When deserializing, you must cast the returned object to the type of the original, as shown in the following example, which deserializes the object into a file (although it could also be deserialized into a stream).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05228-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05228-109">See also</span></span>

- [<span data-ttu-id="05228-110">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="05228-110">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="05228-111">Nasıl yapılır: Bir nesneyi serileştirmek</span><span class="sxs-lookup"><span data-stu-id="05228-111">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
