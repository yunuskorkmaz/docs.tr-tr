---
title: 'Nasıl Yapılır: Nesne Verilerini bir XML Dosyasına Yazma'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 989920709428f0e9cb4ddb8aeacfc71a2df220d2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345973"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="673f7-102">Nasıl yapılır: nesne verilerini bir XML dosyasına yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="673f7-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="673f7-103">Bu örnek, <xref:System.Xml.Serialization.XmlSerializer> sınıfını kullanarak bir sınıftan bir XML dosyasına nesne yazar.</span><span class="sxs-lookup"><span data-stu-id="673f7-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="673f7-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="673f7-104">Example</span></span>  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="673f7-105">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="673f7-105">Compile the code</span></span>  
 <span data-ttu-id="673f7-106">Sınıfın parametresiz ortak bir oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="673f7-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="673f7-107">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="673f7-107">Robust Programming</span></span>  
 <span data-ttu-id="673f7-108">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="673f7-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="673f7-109">Seri hale getirilen sınıfın ortak, parametresiz bir oluşturucusu yok.</span><span class="sxs-lookup"><span data-stu-id="673f7-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="673f7-110">Dosya var ve salt okunurdur (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="673f7-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="673f7-111">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="673f7-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="673f7-112">Disk dolu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="673f7-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="673f7-113">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="673f7-113">.NET Framework Security</span></span>  
 <span data-ttu-id="673f7-114">Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="673f7-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="673f7-115">Bir uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasör için `Create` erişimi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="673f7-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="673f7-116">Dosya zaten mevcutsa, uygulamanın daha az bir ayrıcalığa yalnızca `Write` erişimi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="673f7-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="673f7-117">Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması ve bir klasör için `Create` erişimi yerine yalnızca tek bir dosyaya `Read` erişim izni verilmesi daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="673f7-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="673f7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="673f7-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="673f7-119">Nasıl yapılır: bir XML dosyasından nesne verilerini okuma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="673f7-119">How to: Read Object Data from an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="673f7-120">Serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="673f7-120">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
