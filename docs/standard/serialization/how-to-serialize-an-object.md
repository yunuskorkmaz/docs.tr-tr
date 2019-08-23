---
title: 'Nasıl yapılır: Nesne Serileştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: a587a132446a5f5d74b2d534b1ca3b93ccca1480
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928980"
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="4e518-102">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="4e518-102">How to: Serialize an Object</span></span>
<span data-ttu-id="4e518-103">Bir nesneyi serileştirmek için önce sıralanabilir ve ortak özelliklerini ve alanları ayarlamak için olan nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4e518-103">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="4e518-104">Bunu yapmak için, XML akışının, akış olarak veya dosya olarak depolanacağı aktarım biçimini belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="4e518-104">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="4e518-105">Örneğin, XML akışının kalıcı bir biçimde kaydedilmesi gerekiyorsa, bir <xref:System.IO.FileStream> nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4e518-105">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e518-106">XML serileştirme hakkında daha fazla örnek için bkz. [XML serileştirme örnekleri](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="4e518-106">For more examples of XML serialization, see [Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="4e518-107">Bir nesneyi serileştirmek için</span><span class="sxs-lookup"><span data-stu-id="4e518-107">To serialize an object</span></span>  
  
1. <span data-ttu-id="4e518-108">Nesne oluşturun ve kendi ortak alanları ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4e518-108">Create the object and set its public fields and properties.</span></span>  
  
2. <span data-ttu-id="4e518-109">Nesnesinin türünü <xref:System.Xml.Serialization.XmlSerializer> kullanarak bir oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4e518-109">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="4e518-110">Daha fazla bilgi için bkz <xref:System.Xml.Serialization.XmlSerializer> . sınıf oluşturucuları.</span><span class="sxs-lookup"><span data-stu-id="4e518-110">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3. <span data-ttu-id="4e518-111">Bir xml akışı veya nesnenin ortak özelliklerinin ve alanlarının dosya gösterimini oluşturmak için yönteminiçağırın.<xref:System.Xml.Serialization.XmlSerializer.Serialize%2A></span><span class="sxs-lookup"><span data-stu-id="4e518-111">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="4e518-112">Aşağıdaki örnek, bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4e518-112">The following example creates a file.</span></span>  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new   
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4e518-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e518-113">See also</span></span>

- [<span data-ttu-id="4e518-114">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="4e518-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="4e518-115">Nasıl yapılır: Bir nesnenin serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="4e518-115">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
