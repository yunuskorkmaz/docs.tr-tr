---
title: 'Nasıl yapılır: Nesne verilerini bir XML dosyasına yazma (C#)'
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: 5da79d68bf7e1c955cb6edededb3914bd9c898e5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590692"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a><span data-ttu-id="ba3a9-102">Nasıl yapılır: Nesne verilerini bir XML dosyasına yazma (C#)</span><span class="sxs-lookup"><span data-stu-id="ba3a9-102">How to: Write Object Data to an XML File (C#)</span></span>
<span data-ttu-id="ba3a9-103">Bu örnek, <xref:System.Xml.Serialization.XmlSerializer> sınıfını kullanarak bir sınıftan bir XML dosyasına nesne yazar.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba3a9-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba3a9-104">Example</span></span>  
  
```csharp  
public class XMLWrite  
{  
  
   static void Main(string[] args)  
    {  
        WriteXML();  
    }  
  
    public class Book  
    {  
        public String title;   
    }  
  
    public static void WriteXML()  
    {  
        Book overview = new Book();  
        overview.title = "Serialization Overview";  
        System.Xml.Serialization.XmlSerializer writer =   
            new System.Xml.Serialization.XmlSerializer(typeof(Book));  
  
        var path = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "//SerializationOverview.xml";  
        System.IO.FileStream file = System.IO.File.Create(path);  
  
        writer.Serialize(file, overview);  
        file.Close();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ba3a9-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ba3a9-105">Compiling the Code</span></span>  
 <span data-ttu-id="ba3a9-106">Seri hale getirilen sınıfın parametre içermeyen bir ortak Oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-106">The class being serialized must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ba3a9-107">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="ba3a9-107">Robust Programming</span></span>  
 <span data-ttu-id="ba3a9-108">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="ba3a9-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="ba3a9-109">Seri hale getirilen sınıfın ortak, parametresiz bir oluşturucusu yok.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="ba3a9-110">Dosya var ve salt okunurdur (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="ba3a9-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="ba3a9-111">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="ba3a9-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="ba3a9-112">Disk dolu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="ba3a9-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ba3a9-113">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ba3a9-113">.NET Framework Security</span></span>  
 <span data-ttu-id="ba3a9-114">Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="ba3a9-115">Uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasöre erişmesi gerekir `Create` .</span><span class="sxs-lookup"><span data-stu-id="ba3a9-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="ba3a9-116">Dosya zaten mevcutsa, uygulamanın yalnızca `Write` daha az bir ayrıcalığa erişmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="ba3a9-117">Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması daha güvenlidir ve bir klasör için `Read` `Create` erişim yerine yalnızca tek bir dosyaya erişim izni verir.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba3a9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba3a9-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="ba3a9-119">Nasıl yapılır: XML dosyasından (C#) nesne verilerini okuma</span><span class="sxs-lookup"><span data-stu-id="ba3a9-119">How to: Read Object Data from an XML File (C#)</span></span>](./how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="ba3a9-120">Serileştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="ba3a9-120">Serialization (C#)</span></span>](./index.md)
