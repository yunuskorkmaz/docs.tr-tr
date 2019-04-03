---
title: 'Nasıl yapılır: Nesne verilerini bir XML dosyası (Visual Basic) yazma'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 52b896b0191f29f68cc31e02fc325638ca6341b4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843740"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="cb5c5-102">Nasıl yapılır: Nesne verilerini bir XML dosyası (Visual Basic) yazma</span><span class="sxs-lookup"><span data-stu-id="cb5c5-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="cb5c5-103">Bu örnek, bir XML dosyası kullanmayı öğesinden bir sınıf nesnesi Yazar <xref:System.Xml.Serialization.XmlSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cb5c5-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb5c5-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb5c5-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="cb5c5-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="cb5c5-105">Compiling the Code</span></span>  
 <span data-ttu-id="cb5c5-106">Sınıfı, parametresiz bir ortak oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb5c5-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="cb5c5-107">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="cb5c5-107">Robust Programming</span></span>  
 <span data-ttu-id="cb5c5-108">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="cb5c5-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="cb5c5-109">Serileştirilmekte olan sınıfın ortak, parametresiz bir oluşturucusu yok.</span><span class="sxs-lookup"><span data-stu-id="cb5c5-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="cb5c5-110">Dosya var ve salt okunur (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="cb5c5-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="cb5c5-111">Yol çok uzun (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="cb5c5-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="cb5c5-112">Disk dolu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="cb5c5-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="cb5c5-113">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="cb5c5-113">.NET Framework Security</span></span>  
 <span data-ttu-id="cb5c5-114">Bu örnek, bir dosya zaten mevcut değilse yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb5c5-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="cb5c5-115">Bir uygulama bir dosya oluşturması gerekiyorsa, bu uygulamayı gerekli `Create` klasörü için erişim.</span><span class="sxs-lookup"><span data-stu-id="cb5c5-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="cb5c5-116">Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` erişim, daha az ayrıcalıkla.</span><span class="sxs-lookup"><span data-stu-id="cb5c5-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="cb5c5-117">Mümkün olan yerlerde, dosyayı dağıtım sırasında oluşturmak ve yalnızca vermek için daha güvenli olan `Read` tek bir dosyaya erişimi yerine `Create` erişim için bir klasör.</span><span class="sxs-lookup"><span data-stu-id="cb5c5-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb5c5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb5c5-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="cb5c5-119">Nasıl yapılır: Okuma nesne verilerden bir XML dosyası (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb5c5-119">How to: Read Object Data from an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="cb5c5-120">Seri hale getirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb5c5-120">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
