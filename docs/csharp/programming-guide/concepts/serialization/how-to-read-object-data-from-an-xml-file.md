---
title: "Nasıl yapılır: nesne verilerini bir XML dosyasından (C#) okuma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6a3389de2f3272a546a7380ef386f5d88666e6d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="fa93e-102">Nasıl yapılır: nesne verilerini bir XML dosyasından (C#) okuma</span><span class="sxs-lookup"><span data-stu-id="fa93e-102">How to: Read Object Data from an XML File (C#)</span></span>
<span data-ttu-id="fa93e-103">Bu örnek daha önce bir XML dosyası kullanmaya yazıldı nesne verilerini okur <xref:System.Xml.Serialization.XmlSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fa93e-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa93e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa93e-104">Example</span></span>  
  
```csharp  
public class Book  
{  
    public String title;  
}         
  
public void ReadXML()  
{  
    // First write something so that there is something to read ...  
    var b = new Book { title = "Serialization Overview" };  
    var writer = new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    var wfile = new System.IO.StreamWriter(@"c:\temp\SerializationOverview.xml");  
    writer.Serialize(wfile, b);  
    wfile.Close();  
  
    // Now we can read the serialized book ...  
    System.Xml.Serialization.XmlSerializer reader =   
        new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    System.IO.StreamReader file = new System.IO.StreamReader(  
        @"c:\temp\SerializationOverview.xml");  
    Book overview =  (Book)reader.Deserialize(file);  
    file.Close();  
  
    Console.WriteLine(overview.title);  
  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fa93e-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fa93e-105">Compiling the Code</span></span>  
 <span data-ttu-id="fa93e-106">Dosya adı "c:\temp\SerializationOverview.xml" serileştirilmiş verilerini içeren dosyanın adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="fa93e-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="fa93e-107">Verileri seri hale getirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: nesne verilerini bir XML dosyasına (C#) yazma](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="fa93e-107">For more information about serializing data, see [How to: Write Object Data to an XML File (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="fa93e-108">Sınıf parametresiz ortak bir oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fa93e-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="fa93e-109">Yalnızca genel özellikleri ve alanları serisi.</span><span class="sxs-lookup"><span data-stu-id="fa93e-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fa93e-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="fa93e-110">Robust Programming</span></span>  
 <span data-ttu-id="fa93e-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="fa93e-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="fa93e-112">Serileştirilen sınıfı genel, parametresiz bir oluşturucu yok.</span><span class="sxs-lookup"><span data-stu-id="fa93e-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="fa93e-113">Veri dosyasındaki verileri seri durumdan çıkarılacak sınıfından temsil etmiyor.</span><span class="sxs-lookup"><span data-stu-id="fa93e-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="fa93e-114">Dosya yok (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="fa93e-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fa93e-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="fa93e-115">.NET Framework Security</span></span>  
 <span data-ttu-id="fa93e-116">Her zaman girişleri doğrulayın ve hiçbir zaman güvenilmeyen bir kaynaktan veri serisi.</span><span class="sxs-lookup"><span data-stu-id="fa93e-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="fa93e-117">Yeniden oluşturulan nesne, seri durumdan kod izinleriyle yerel bir bilgisayarda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="fa93e-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="fa93e-118">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="fa93e-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa93e-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa93e-119">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="fa93e-120">Nasıl yapılır: nesne verilerini bir XML dosyasına (C#) yazma</span><span class="sxs-lookup"><span data-stu-id="fa93e-120">How to: Write Object Data to an XML File (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 [<span data-ttu-id="fa93e-121">Seri hale getirme (C#)</span><span class="sxs-lookup"><span data-stu-id="fa93e-121">Serialization (C# )</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)  
 [<span data-ttu-id="fa93e-122">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fa93e-122">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
