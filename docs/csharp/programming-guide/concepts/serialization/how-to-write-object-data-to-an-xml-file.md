---
title: 'Nasıl yapılır: Nesne verilerini bir XML dosyasına yazma (C#)'
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: 064d7ed61921f3f700311a1b09ee77e0c9818d71
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554289"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a><span data-ttu-id="b8e6f-102">Nasıl yapılır: Nesne verilerini bir XML dosyasına yazma (C#)</span><span class="sxs-lookup"><span data-stu-id="b8e6f-102">How to: Write Object Data to an XML File (C#)</span></span>
<span data-ttu-id="b8e6f-103">Bu örnek, bir XML dosyası kullanmayı öğesinden bir sınıf nesnesi Yazar <xref:System.Xml.Serialization.XmlSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8e6f-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8e6f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8e6f-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="b8e6f-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b8e6f-105">Compiling the Code</span></span>  
 <span data-ttu-id="b8e6f-106">Sınıfı, parametresiz bir ortak oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8e6f-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b8e6f-107">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="b8e6f-107">Robust Programming</span></span>  
 <span data-ttu-id="b8e6f-108">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="b8e6f-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="b8e6f-109">Serileştirilmekte olan sınıfın ortak, parametresiz bir oluşturucusu yok.</span><span class="sxs-lookup"><span data-stu-id="b8e6f-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="b8e6f-110">Dosya var ve salt okunur (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="b8e6f-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="b8e6f-111">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="b8e6f-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="b8e6f-112">Disk dolu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="b8e6f-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b8e6f-113">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b8e6f-113">.NET Framework Security</span></span>  
 <span data-ttu-id="b8e6f-114">Bu örnek, bir dosya zaten mevcut değilse yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b8e6f-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="b8e6f-115">Bir uygulama bir dosya oluşturması gerekiyorsa, bu uygulamayı gerekli `Create` klasörü için erişim.</span><span class="sxs-lookup"><span data-stu-id="b8e6f-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="b8e6f-116">Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` erişim, daha az ayrıcalıkla.</span><span class="sxs-lookup"><span data-stu-id="b8e6f-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="b8e6f-117">Mümkün olan yerlerde, dosyayı dağıtım sırasında oluşturmak ve yalnızca vermek için daha güvenli olan `Read` tek bir dosyaya erişimi yerine `Create` erişim için bir klasör.</span><span class="sxs-lookup"><span data-stu-id="b8e6f-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e6f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8e6f-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="b8e6f-119">Nasıl yapılır: Nesne verilerini bir XML dosyasından okuma (C#)</span><span class="sxs-lookup"><span data-stu-id="b8e6f-119">How to: Read Object Data from an XML File (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="b8e6f-120">Seri hale getirme (C#)</span><span class="sxs-lookup"><span data-stu-id="b8e6f-120">Serialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)
