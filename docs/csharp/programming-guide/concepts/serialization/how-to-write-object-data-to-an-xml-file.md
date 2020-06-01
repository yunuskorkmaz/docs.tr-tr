---
title: Nesne verilerini bir XML dosyasına yazma (C#)
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: 6f18ae194d2ed70f633665a29772622319ea9493
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84242000"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a><span data-ttu-id="f04c0-102">Nesne verilerini bir XML dosyasına yazma (C#)</span><span class="sxs-lookup"><span data-stu-id="f04c0-102">How to write object data to an XML file (C#)</span></span>
<span data-ttu-id="f04c0-103">Bu örnek, sınıfını kullanarak bir sınıftan bir XML dosyasına nesne yazar <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="f04c0-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f04c0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f04c0-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="f04c0-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f04c0-105">Compiling the Code</span></span>  
 <span data-ttu-id="f04c0-106">Seri hale getirilen sınıfın parametre içermeyen bir ortak Oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f04c0-106">The class being serialized must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f04c0-107">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="f04c0-107">Robust Programming</span></span>  
 <span data-ttu-id="f04c0-108">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="f04c0-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="f04c0-109">Seri hale getirilen sınıfın ortak, parametresiz bir oluşturucusu yok.</span><span class="sxs-lookup"><span data-stu-id="f04c0-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="f04c0-110">Dosya var ve salt okunurdur ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="f04c0-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="f04c0-111">Yol çok uzun ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="f04c0-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="f04c0-112">Disk dolu ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="f04c0-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="f04c0-113">.NET güvenliği</span><span class="sxs-lookup"><span data-stu-id="f04c0-113">.NET Security</span></span>  
 <span data-ttu-id="f04c0-114">Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f04c0-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="f04c0-115">Uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın `Create` klasöre erişmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f04c0-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="f04c0-116">Dosya zaten mevcutsa, uygulamanın yalnızca daha `Write` az bir ayrıcalığa erişmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f04c0-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="f04c0-117">Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması daha güvenlidir ve `Read` `Create` bir klasör için erişim yerine yalnızca tek bir dosyaya erişim izni verir.</span><span class="sxs-lookup"><span data-stu-id="f04c0-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f04c0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f04c0-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="f04c0-119">XML dosyasından nesne verilerini okuma (C#)</span><span class="sxs-lookup"><span data-stu-id="f04c0-119">How to read object data from an XML file (C#)</span></span>](./how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="f04c0-120">Serileştirme (C# )</span><span class="sxs-lookup"><span data-stu-id="f04c0-120">Serialization (C#)</span></span>](./index.md)
