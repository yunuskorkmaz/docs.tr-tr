---
title: "Nasıl yapılır: bir nesneyi serileştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1ce7baf12c1826ddd14edad5e7dec328278c40e3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="dc476-102">Nasıl yapılır: bir nesneyi serileştirme</span><span class="sxs-lookup"><span data-stu-id="dc476-102">How to: Serialize an Object</span></span>
<span data-ttu-id="dc476-103">Bir nesneyi serileştirmek için önce sıralanabilir ve ortak özelliklerini ve alanları ayarlamak için olan nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dc476-103">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="dc476-104">Bunu yapmak için XML akışı bir akış veya bir dosya olarak depolanmasını aktarım biçimi belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc476-104">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="dc476-105">Örneğin, XML Akışı kalıcı bir biçimde kaydedilmelidir varsa, oluşturun bir <xref:System.IO.FileStream> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="dc476-105">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc476-106">Daha fazla XML serileştirme örnekleri için bkz: [XML serileştirme örnekler](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="dc476-106">For more examples of XML serialization, see [Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="dc476-107">Bir nesneyi serileştirmek için</span><span class="sxs-lookup"><span data-stu-id="dc476-107">To serialize an object</span></span>  
  
1.  <span data-ttu-id="dc476-108">Nesne oluşturun ve kendi ortak alanları ve özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="dc476-108">Create the object and set its public fields and properties.</span></span>  
  
2.  <span data-ttu-id="dc476-109">Oluşturmak bir <xref:System.Xml.Serialization.XmlSerializer> nesne türünü kullanarak.</span><span class="sxs-lookup"><span data-stu-id="dc476-109">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="dc476-110">Daha fazla bilgi için bkz: <xref:System.Xml.Serialization.XmlSerializer> sınıf oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="dc476-110">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3.  <span data-ttu-id="dc476-111">Çağrı <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> bir XML akışı veya bir dosya gösterimini nesnenin genel özellikleri ve alanları oluşturmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="dc476-111">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="dc476-112">Aşağıdaki örnek, bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dc476-112">The following example creates a file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc476-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc476-113">See Also</span></span>  
 [<span data-ttu-id="dc476-114">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="dc476-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="dc476-115">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="dc476-115">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
