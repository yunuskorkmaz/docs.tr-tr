---
title: 'Nasıl yapılır: bir nesneyi serileştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: b979d63132b44ee2e05fcc55cfdd4c79309a159b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581452"
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="b3e7a-102">Nasıl yapılır: bir nesneyi serileştirme</span><span class="sxs-lookup"><span data-stu-id="b3e7a-102">How to: Serialize an Object</span></span>
<span data-ttu-id="b3e7a-103">Bir nesneyi serileştirmek için önce sıralanabilir ve ortak özelliklerini ve alanları ayarlamak için olan nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b3e7a-103">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="b3e7a-104">Bunu yapmak için XML akışı bir akış veya bir dosya olarak depolanmasını aktarım biçimi belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b3e7a-104">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="b3e7a-105">Örneğin, XML Akışı kalıcı bir biçimde kaydedilmelidir varsa, oluşturun bir <xref:System.IO.FileStream> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b3e7a-105">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3e7a-106">Daha fazla XML serileştirme örnekleri için bkz: [XML serileştirme örnekler](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="b3e7a-106">For more examples of XML serialization, see [Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="b3e7a-107">Bir nesneyi serileştirmek için</span><span class="sxs-lookup"><span data-stu-id="b3e7a-107">To serialize an object</span></span>  
  
1.  <span data-ttu-id="b3e7a-108">Nesne oluşturun ve kendi ortak alanları ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b3e7a-108">Create the object and set its public fields and properties.</span></span>  
  
2.  <span data-ttu-id="b3e7a-109">Oluşturmak bir <xref:System.Xml.Serialization.XmlSerializer> nesne türünü kullanarak.</span><span class="sxs-lookup"><span data-stu-id="b3e7a-109">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="b3e7a-110">Daha fazla bilgi için bkz: <xref:System.Xml.Serialization.XmlSerializer> sınıf oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="b3e7a-110">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3.  <span data-ttu-id="b3e7a-111">Çağrı <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> bir XML akışı veya bir dosya gösterimini nesnenin genel özellikleri ve alanları oluşturmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="b3e7a-111">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="b3e7a-112">Aşağıdaki örnek, bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b3e7a-112">The following example creates a file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3e7a-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3e7a-113">See Also</span></span>  
 [<span data-ttu-id="b3e7a-114">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="b3e7a-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="b3e7a-115">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="b3e7a-115">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
