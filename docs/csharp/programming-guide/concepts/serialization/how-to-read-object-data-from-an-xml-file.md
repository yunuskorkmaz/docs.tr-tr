---
title: 'Nasıl yapılır: Nesne verilerini bir XML dosyasından okuma (C#)'
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 33e4395c2be421385948d256a989d06ac215c9c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583492"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="d156b-102">Nasıl yapılır: Nesne verilerini bir XML dosyasından okuma (C#)</span><span class="sxs-lookup"><span data-stu-id="d156b-102">How to: Read Object Data from an XML File (C#)</span></span>
<span data-ttu-id="d156b-103">Bu örnek daha önce bir XML dosyası kullanmayı yazılmış nesne verilerini okur <xref:System.Xml.Serialization.XmlSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d156b-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d156b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d156b-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="d156b-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d156b-105">Compiling the Code</span></span>  
 <span data-ttu-id="d156b-106">Dosya adı "c:\temp\SerializationOverview.xml" seri hale getirilmiş veri içeren dosyanın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d156b-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="d156b-107">Verileri seri hale getirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Nesne verilerini bir XML dosyasına yazma (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="d156b-107">For more information about serializing data, see [How to: Write Object Data to an XML File (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="d156b-108">Sınıfı, parametresiz bir ortak oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d156b-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="d156b-109">Yalnızca ortak özellikler ve alanları seri.</span><span class="sxs-lookup"><span data-stu-id="d156b-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d156b-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d156b-110">Robust Programming</span></span>  
 <span data-ttu-id="d156b-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="d156b-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="d156b-112">Serileştirilmekte olan sınıfın ortak, parametresiz bir oluşturucusu yok.</span><span class="sxs-lookup"><span data-stu-id="d156b-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="d156b-113">Dosyasındaki verilerin veri seri durumdan sınıftan temsil etmiyor.</span><span class="sxs-lookup"><span data-stu-id="d156b-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="d156b-114">Dosya yok (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="d156b-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d156b-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d156b-115">.NET Framework Security</span></span>  
 <span data-ttu-id="d156b-116">Her zaman girişleri doğrulayın ve hiçbir zaman güvenilmeyen bir kaynaktan gelen verileri seri durumdan.</span><span class="sxs-lookup"><span data-stu-id="d156b-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="d156b-117">Yeniden oluşturulan nesne, seri durumdan kodun izinlere sahip bir yerel bilgisayarda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="d156b-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="d156b-118">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="d156b-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d156b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d156b-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="d156b-120">Nasıl yapılır: Nesne verilerini bir XML dosyasına yazma (C#)</span><span class="sxs-lookup"><span data-stu-id="d156b-120">How to: Write Object Data to an XML File (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="d156b-121">Seri hale getirme (C#)</span><span class="sxs-lookup"><span data-stu-id="d156b-121">Serialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)
- [<span data-ttu-id="d156b-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d156b-122">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
