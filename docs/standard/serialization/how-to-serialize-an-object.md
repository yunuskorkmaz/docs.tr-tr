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
ms.openlocfilehash: e9c7ba250995db1c7a701de346b18661892e7e23
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291558"
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="ea713-104">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="ea713-104">How to: Serialize an Object</span></span>
<span data-ttu-id="ea713-105">Bir nesneyi serileştirmek için önce sıralanabilir ve ortak özelliklerini ve alanları ayarlamak için olan nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ea713-105">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="ea713-106">Bunu yapmak için, XML akışının, akış olarak veya dosya olarak depolanacağı aktarım biçimini belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ea713-106">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="ea713-107">Örneğin, XML akışının kalıcı bir biçimde kaydedilmesi gerekiyorsa, bir <xref:System.IO.FileStream> nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ea713-107">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea713-108">XML serileştirme hakkında daha fazla örnek için bkz. [XML serileştirme örnekleri](examples-of-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="ea713-108">For more examples of XML serialization, see [Examples of XML Serialization](examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="ea713-109">Bir nesneyi serileştirmek için</span><span class="sxs-lookup"><span data-stu-id="ea713-109">To serialize an object</span></span>  
  
1. <span data-ttu-id="ea713-110">Nesne oluşturun ve kendi ortak alanları ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ea713-110">Create the object and set its public fields and properties.</span></span>  
  
2. <span data-ttu-id="ea713-111"><xref:System.Xml.Serialization.XmlSerializer>Nesnesinin türünü kullanarak bir oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ea713-111">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="ea713-112">Daha fazla bilgi için bkz <xref:System.Xml.Serialization.XmlSerializer> . sınıf oluşturucuları.</span><span class="sxs-lookup"><span data-stu-id="ea713-112">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3. <span data-ttu-id="ea713-113"><xref:System.Xml.Serialization.XmlSerializer.Serialize%2A>BIR XML akışı veya nesnenin ortak özelliklerinin ve alanlarının dosya gösterimini oluşturmak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="ea713-113">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="ea713-114">Aşağıdaki örnek, bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ea713-114">The following example creates a file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ea713-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea713-115">See also</span></span>

- [<span data-ttu-id="ea713-116">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="ea713-116">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="ea713-117">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="ea713-117">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
