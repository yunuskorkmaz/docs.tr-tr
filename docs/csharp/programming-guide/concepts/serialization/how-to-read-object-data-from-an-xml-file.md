---
title: XML dosyasından nesne verilerini okuma (C#)
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 2da5919c11ed2d6e43f4f9fc406f43e3ed48060f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346430"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="ca6b7-102">XML dosyasından nesne verilerini okuma (C#)</span><span class="sxs-lookup"><span data-stu-id="ca6b7-102">How to read object data from an XML file (C#)</span></span>
<span data-ttu-id="ca6b7-103">Bu örnek, daha önce <xref:System.Xml.Serialization.XmlSerializer> sınıfını kullanarak bir XML dosyasına yazılmış nesne verilerini okur.</span><span class="sxs-lookup"><span data-stu-id="ca6b7-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca6b7-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ca6b7-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ca6b7-105">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="ca6b7-105">Compiling the Code</span></span>  
<span data-ttu-id="ca6b7-106">"C:\temp\SerializationOverview.xml" dosya adını seri hale getirilen verileri içeren dosyanın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ca6b7-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="ca6b7-107">Verileri serileştirme hakkında daha fazla bilgi için bkz. [BIR XML dosyasına nesne verileri yazmaC#()](./how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="ca6b7-107">For more information about serializing data, see [How to write object data to an XML file (C#)](./how-to-write-object-data-to-an-xml-file.md).</span></span>
  
 <span data-ttu-id="ca6b7-108">Sınıfın parametresiz ortak bir oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ca6b7-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="ca6b7-109">Yalnızca ortak özellikler ve alanların serisi kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ca6b7-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ca6b7-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="ca6b7-110">Robust Programming</span></span>  
 <span data-ttu-id="ca6b7-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="ca6b7-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="ca6b7-112">Seri hale getirilen sınıfın ortak, parametresiz bir oluşturucusu yok.</span><span class="sxs-lookup"><span data-stu-id="ca6b7-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="ca6b7-113">Dosyadaki veriler, seri durumdan çıkarılacak sınıftan verileri temsil etmez.</span><span class="sxs-lookup"><span data-stu-id="ca6b7-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="ca6b7-114">Dosya yok (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="ca6b7-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ca6b7-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ca6b7-115">.NET Framework Security</span></span>  
 <span data-ttu-id="ca6b7-116">Girişleri her zaman doğrulayın ve güvenilmeyen bir kaynaktaki verileri hiçbir zaman serisini kaldırma.</span><span class="sxs-lookup"><span data-stu-id="ca6b7-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="ca6b7-117">Yeniden oluşturulan nesne, yerel bir bilgisayarda, serisi kaldırılan kodun izinleriyle çalışır.</span><span class="sxs-lookup"><span data-stu-id="ca6b7-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="ca6b7-118">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="ca6b7-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca6b7-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca6b7-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="ca6b7-120">Nesne verilerini bir XML dosyasına yazma (C#)</span><span class="sxs-lookup"><span data-stu-id="ca6b7-120">How to write object data to an XML file (C#)</span></span>](./how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="ca6b7-121">Serileştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="ca6b7-121">Serialization (C#)</span></span>](./index.md)
- [<span data-ttu-id="ca6b7-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ca6b7-122">C# Programming Guide</span></span>](../../index.md)
