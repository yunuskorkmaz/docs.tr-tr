---
title: 'Nasıl yapılır: Okuma nesne verilerden bir XML dosyası (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: f6233fc7ce74cbd39237bab07cfd2ed22b9c2240
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834900"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="f35af-102">Nasıl yapılır: Okuma nesne verilerden bir XML dosyası (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f35af-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="f35af-103">Bu örnek daha önce bir XML dosyası kullanmayı yazılmış nesne verilerini okur <xref:System.Xml.Serialization.XmlSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f35af-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f35af-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f35af-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="f35af-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f35af-105">Compiling the Code</span></span>  
 <span data-ttu-id="f35af-106">Dosya adı "c:\temp\SerializationOverview.xml" seri hale getirilmiş veri içeren dosyanın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f35af-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="f35af-107">Verileri seri hale getirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Nesne verilerini bir XML dosyası (Visual Basic) yazma](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="f35af-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="f35af-108">Sınıfı, parametresiz bir ortak oluşturucuya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f35af-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="f35af-109">Yalnızca ortak özellikler ve alanları seri.</span><span class="sxs-lookup"><span data-stu-id="f35af-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f35af-110">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="f35af-110">Robust Programming</span></span>  
 <span data-ttu-id="f35af-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="f35af-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f35af-112">Serileştirilmekte olan sınıfın ortak, parametresiz bir oluşturucusu yok.</span><span class="sxs-lookup"><span data-stu-id="f35af-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="f35af-113">Dosyasındaki verilerin veri seri durumdan sınıftan temsil etmiyor.</span><span class="sxs-lookup"><span data-stu-id="f35af-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="f35af-114">Dosya yok (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="f35af-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f35af-115">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="f35af-115">.NET Framework Security</span></span>  
 <span data-ttu-id="f35af-116">Her zaman girişleri doğrulayın ve hiçbir zaman güvenilmeyen bir kaynaktan gelen verileri seri durumdan.</span><span class="sxs-lookup"><span data-stu-id="f35af-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="f35af-117">Yeniden oluşturulan nesne, seri durumdan kodun izinlere sahip bir yerel bilgisayarda çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="f35af-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="f35af-118">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="f35af-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f35af-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f35af-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="f35af-120">Nasıl yapılır: Nesne verilerini bir XML dosyası (Visual Basic) yazma</span><span class="sxs-lookup"><span data-stu-id="f35af-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="f35af-121">Seri hale getirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f35af-121">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [<span data-ttu-id="f35af-122">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f35af-122">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
