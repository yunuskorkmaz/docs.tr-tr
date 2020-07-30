---
title: XML dosyasından nesne verilerini okuma (C#)
description: Bu C# örneği, daha önce XmlSerializer sınıfını kullanarak bir XML dosyasına yazılmış nesne verilerini okur.
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 525a93812279756b3802d43d85bb5e61d8f7415e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302795"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="b103a-103">XML dosyasından nesne verilerini okuma (C#)</span><span class="sxs-lookup"><span data-stu-id="b103a-103">How to read object data from an XML file (C#)</span></span>
<span data-ttu-id="b103a-104">Bu örnek, daha önce sınıfını kullanarak bir XML dosyasına yazılmış nesne verilerini okur <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="b103a-104">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b103a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b103a-105">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="b103a-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b103a-106">Compiling the Code</span></span>  
<span data-ttu-id="b103a-107">"c:\temp\SerializationOverview.xml" dosya adını seri hale getirilen verileri içeren dosyanın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b103a-107">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="b103a-108">Verileri seri hale getirme hakkında daha fazla bilgi için bkz. [BIR XML dosyasına nesne verileri yazma (C#)](./how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="b103a-108">For more information about serializing data, see [How to write object data to an XML file (C#)](./how-to-write-object-data-to-an-xml-file.md).</span></span>
  
 <span data-ttu-id="b103a-109">Sınıfın parametresiz ortak bir oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b103a-109">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="b103a-110">Yalnızca ortak özellikler ve alanların serisi kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b103a-110">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b103a-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="b103a-111">Robust Programming</span></span>  
 <span data-ttu-id="b103a-112">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="b103a-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="b103a-113">Seri hale getirilen sınıfın ortak, parametresiz bir oluşturucusu yok.</span><span class="sxs-lookup"><span data-stu-id="b103a-113">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="b103a-114">Dosyadaki veriler, seri durumdan çıkarılacak sınıftan verileri temsil etmez.</span><span class="sxs-lookup"><span data-stu-id="b103a-114">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="b103a-115">Dosya yok ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="b103a-115">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="b103a-116">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="b103a-116">.NET Security</span></span>  
 <span data-ttu-id="b103a-117">Girişleri her zaman doğrulayın ve güvenilmeyen bir kaynaktaki verileri hiçbir zaman serisini kaldırma.</span><span class="sxs-lookup"><span data-stu-id="b103a-117">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="b103a-118">Yeniden oluşturulan nesne, yerel bir bilgisayarda, serisi kaldırılan kodun izinleriyle çalışır.</span><span class="sxs-lookup"><span data-stu-id="b103a-118">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="b103a-119">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="b103a-119">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b103a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b103a-120">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="b103a-121">Nesne verilerini bir XML dosyasına yazma (C#)</span><span class="sxs-lookup"><span data-stu-id="b103a-121">How to write object data to an XML file (C#)</span></span>](./how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="b103a-122">Serileştirme (C# )</span><span class="sxs-lookup"><span data-stu-id="b103a-122">Serialization (C#)</span></span>](./index.md)
- [<span data-ttu-id="b103a-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b103a-123">C# Programming Guide</span></span>](../../index.md)
