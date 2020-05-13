---
title: 'Nasıl yapılır: Nesne Serileştirme'
description: Bu makalede bir nesnenin serileştirilme yöntemi gösterilmektedir. XML akışının, akış olarak veya dosya olarak depolandığı bir aktarım biçimi seçin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: 63446df3fa2c931c839eda91c648cee961715f93
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377551"
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="ff081-104">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="ff081-104">How to: Serialize an Object</span></span>
<span data-ttu-id="ff081-105">Bir nesneyi serileştirmek için önce sıralanabilir ve ortak özelliklerini ve alanları ayarlamak için olan nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ff081-105">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="ff081-106">Bunu yapmak için, XML akışının, akış olarak veya dosya olarak depolanacağı aktarım biçimini belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ff081-106">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="ff081-107">Örneğin, XML akışının kalıcı bir biçimde kaydedilmesi gerekiyorsa, bir <xref:System.IO.FileStream> nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ff081-107">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff081-108">XML serileştirme hakkında daha fazla örnek için bkz. [XML serileştirme örnekleri](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="ff081-108">For more examples of XML serialization, see [Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="ff081-109">Bir nesneyi serileştirmek için</span><span class="sxs-lookup"><span data-stu-id="ff081-109">To serialize an object</span></span>  
  
1. <span data-ttu-id="ff081-110">Nesne oluşturun ve kendi ortak alanları ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ff081-110">Create the object and set its public fields and properties.</span></span>  
  
2. <span data-ttu-id="ff081-111"><xref:System.Xml.Serialization.XmlSerializer>Nesnesinin türünü kullanarak bir oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ff081-111">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="ff081-112">Daha fazla bilgi için bkz <xref:System.Xml.Serialization.XmlSerializer> . sınıf oluşturucuları.</span><span class="sxs-lookup"><span data-stu-id="ff081-112">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3. <span data-ttu-id="ff081-113"><xref:System.Xml.Serialization.XmlSerializer.Serialize%2A>BIR XML akışı veya nesnenin ortak özelliklerinin ve alanlarının dosya gösterimini oluşturmak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="ff081-113">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="ff081-114">Aşağıdaki örnek, bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ff081-114">The following example creates a file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ff081-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff081-115">See also</span></span>

- [<span data-ttu-id="ff081-116">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="ff081-116">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="ff081-117">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="ff081-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
