---
title: XML dosyasından nesne verileri nasıl okunur (C#)
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 18428cbe2f2d3b9434a77ee4d063ceabbba6bcb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167824"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="70faf-102">XML dosyasından nesne verileri nasıl okunur (C#)</span><span class="sxs-lookup"><span data-stu-id="70faf-102">How to read object data from an XML file (C#)</span></span>
<span data-ttu-id="70faf-103">Bu örnek, <xref:System.Xml.Serialization.XmlSerializer> sınıfı kullanarak daha önce bir XML dosyasına yazılmış nesne verilerini okur.</span><span class="sxs-lookup"><span data-stu-id="70faf-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70faf-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="70faf-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="70faf-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="70faf-105">Compiling the Code</span></span>  
<span data-ttu-id="70faf-106">"c:\temp\SerializationOverview.xml" dosya adını serileştirilmiş verileri içeren dosyanın adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="70faf-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="70faf-107">Verileri serileştirme hakkında daha fazla bilgi için, [nesne verilerinin XML dosyasına (C#) nasıl yazılması](./how-to-write-object-data-to-an-xml-file.md)nabakını görün.</span><span class="sxs-lookup"><span data-stu-id="70faf-107">For more information about serializing data, see [How to write object data to an XML file (C#)](./how-to-write-object-data-to-an-xml-file.md).</span></span>
  
 <span data-ttu-id="70faf-108">Sınıfın parametreleri olmayan bir ortak oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="70faf-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="70faf-109">Yalnızca ortak özellikler ve alanlar deserialized vardır.</span><span class="sxs-lookup"><span data-stu-id="70faf-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="70faf-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="70faf-110">Robust Programming</span></span>  
 <span data-ttu-id="70faf-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="70faf-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="70faf-112">Serihale edilen sınıfın ortak, parametresiz bir oluşturucusu yoktur.</span><span class="sxs-lookup"><span data-stu-id="70faf-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="70faf-113">Dosyadaki veriler, seri olmaktan çıkarılacak sınıftaki verileri temsil etmez.</span><span class="sxs-lookup"><span data-stu-id="70faf-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="70faf-114">Dosya yok (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="70faf-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="70faf-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="70faf-115">.NET Framework Security</span></span>  
 <span data-ttu-id="70faf-116">Girişleri her zaman doğrulayın ve güvenilmeyen bir kaynaktan gelen verileri asla deserialize edin.</span><span class="sxs-lookup"><span data-stu-id="70faf-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="70faf-117">Yeniden oluşturulan nesne, onu deserialize eden kodun izinleriyle yerel bir bilgisayarda çalışır.</span><span class="sxs-lookup"><span data-stu-id="70faf-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="70faf-118">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="70faf-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70faf-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70faf-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="70faf-120">Bir XML dosyasına nesne verileri yazma (C#)</span><span class="sxs-lookup"><span data-stu-id="70faf-120">How to write object data to an XML file (C#)</span></span>](./how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="70faf-121">Serileştirme (C# )</span><span class="sxs-lookup"><span data-stu-id="70faf-121">Serialization (C#)</span></span>](./index.md)
- [<span data-ttu-id="70faf-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="70faf-122">C# Programming Guide</span></span>](../../index.md)
