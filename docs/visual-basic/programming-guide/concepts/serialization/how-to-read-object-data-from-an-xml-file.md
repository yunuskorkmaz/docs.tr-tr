---
title: 'Nasıl Yapılır: Nesne Verilerini bir XML Dosyasından Okuma'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: efd5fb72487c92bcccf1fc797106f93c0d2a39fc
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345989"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="c6169-102">Nasıl yapılır: bir XML dosyasından nesne verilerini okuma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6169-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="c6169-103">Bu örnek, daha önce <xref:System.Xml.Serialization.XmlSerializer> sınıfını kullanarak bir XML dosyasına yazılmış nesne verilerini okur.</span><span class="sxs-lookup"><span data-stu-id="c6169-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6169-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6169-104">Example</span></span>  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="c6169-105">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="c6169-105">Compile the code</span></span>  
 <span data-ttu-id="c6169-106">"C:\temp\SerializationOverview.xml" dosya adını seri hale getirilen verileri içeren dosyanın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c6169-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="c6169-107">Verileri serileştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: nesne verilerini BIR XML dosyasına yazma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="c6169-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="c6169-108">Sınıfın parametresiz ortak bir oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c6169-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="c6169-109">Yalnızca ortak özellikler ve alanların serisi kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c6169-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c6169-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c6169-110">Robust Programming</span></span>  
 <span data-ttu-id="c6169-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="c6169-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="c6169-112">Seri hale getirilen sınıfın ortak, parametresiz bir oluşturucusu yok.</span><span class="sxs-lookup"><span data-stu-id="c6169-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="c6169-113">Dosyadaki veriler, seri durumdan çıkarılacak sınıftan verileri temsil etmez.</span><span class="sxs-lookup"><span data-stu-id="c6169-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="c6169-114">Dosya yok (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="c6169-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c6169-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c6169-115">.NET Framework Security</span></span>  
 <span data-ttu-id="c6169-116">Girişleri her zaman doğrulayın ve güvenilmeyen bir kaynaktaki verileri hiçbir zaman serisini kaldırma.</span><span class="sxs-lookup"><span data-stu-id="c6169-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="c6169-117">Yeniden oluşturulan nesne, yerel bir bilgisayarda, serisi kaldırılan kodun izinleriyle çalışır.</span><span class="sxs-lookup"><span data-stu-id="c6169-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="c6169-118">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="c6169-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6169-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6169-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="c6169-120">Nasıl yapılır: nesne verilerini bir XML dosyasına yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6169-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="c6169-121">Serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6169-121">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [<span data-ttu-id="c6169-122">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c6169-122">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
