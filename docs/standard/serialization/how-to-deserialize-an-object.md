---
title: XmlSerializer kullanarak bir nesne serisini kaldırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: c24ba466a208fe5abdbf565169c41c4ee3f47482
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559904"
---
# <a name="how-to-deserialize-an-object-using-xmlserializer"></a><span data-ttu-id="e011a-102">XmlSerializer kullanarak bir nesne serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="e011a-102">How to deserialize an object using XmlSerializer</span></span>

<span data-ttu-id="e011a-103">Bir nesnenin serisini kaldırdığınızda, aktarım biçimi bir akış veya dosya nesnesi oluşturup oluşturamayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="e011a-103">When you deserialize an object, the transport format determines whether you will create a stream or file object.</span></span> <span data-ttu-id="e011a-104">Aktarım biçimi saptandıktan sonra, <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> veya <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> yöntemlerini gerektiği şekilde çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e011a-104">After the transport format is determined, you can call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> or <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> methods, as required.</span></span>

## <a name="to-deserialize-an-object"></a><span data-ttu-id="e011a-105">Bir nesnenin serisini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="e011a-105">To deserialize an object</span></span>

1. <span data-ttu-id="e011a-106">Seri durumdan <xref:System.Xml.Serialization.XmlSerializer> çıkarılacak nesnenin türünü kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e011a-106">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object to deserialize.</span></span>

1. <span data-ttu-id="e011a-107">Arama <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> nesnenin bir kopyasını oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e011a-107">Call the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> method to produce a replica of the object.</span></span> <span data-ttu-id="e011a-108">Seri durumdan çıkarma sırasında döndürülen nesneyi, aşağıdaki örnekte gösterildiği gibi, bir dosyanın bir dosyadan serileştirerek (bir akıştan seri durumdan çıkarılabilse de), bu nesnenin özgün türüne atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="e011a-108">When deserializing, you must cast the returned object to the type of the original, as shown in the following example, which deserializes the object from a file (although it could also be deserialized from a stream).</span></span>

    ```vb
    ' Construct an instance of the XmlSerializer with the type
    ' of object that is being deserialized.
    Dim mySerializer As New XmlSerializer(GetType(MySerializableClass))
    ' To read the file, create a FileStream.
    Dim myFileStream As New FileStream("myFileName.xml", FileMode.Open)
    ' Call the Deserialize method and cast to the object type.
    Dim myObject = CType( _
    mySerializer.Deserialize(myFileStream), MySerializableClass)
    ```

    ```csharp
    // Construct an instance of the XmlSerializer with the type
    // of object that is being deserialized.
    var mySerializer = new XmlSerializer(typeof(MySerializableClass));
    // To read the file, create a FileStream.
    var myFileStream = new FileStream("myFileName.xml", FileMode.Open);
    // Call the Deserialize method and cast to the object type.
    var myObject = (MySerializableClass) mySerializer.Deserialize(myFileStream)
    ```

## <a name="see-also"></a><span data-ttu-id="e011a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e011a-109">See also</span></span>

- [<span data-ttu-id="e011a-110">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="e011a-110">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="e011a-111">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e011a-111">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
