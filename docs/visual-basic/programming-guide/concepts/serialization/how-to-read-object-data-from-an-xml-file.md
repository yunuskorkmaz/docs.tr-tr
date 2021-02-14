---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: nesne verilerini bir XML dosyasından okuma (Visual Basic)'
title: 'Nasıl Yapılır: Nesne Verilerini bir XML Dosyasından Okuma'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: d281997a0dd96ad6263fe03cea84b3e84005a3ad
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486829"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="899a5-103">Nasıl yapılır: bir XML dosyasından nesne verilerini okuma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="899a5-103">How to: Read Object Data from an XML File (Visual Basic)</span></span>

<span data-ttu-id="899a5-104">Bu örnek, daha önce sınıfını kullanarak bir XML dosyasına yazılmış nesne verilerini okur <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="899a5-104">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="899a5-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="899a5-105">Example</span></span>  
  
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
  
## <a name="compile-the-code"></a><span data-ttu-id="899a5-106">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="899a5-106">Compile the code</span></span>  

 <span data-ttu-id="899a5-107">"c:\temp\SerializationOverview.xml" dosya adını seri hale getirilen verileri içeren dosyanın adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="899a5-107">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="899a5-108">Verileri serileştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: nesne verilerini BIR XML dosyasına yazma (Visual Basic)](how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="899a5-108">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="899a5-109">Sınıfın parametresiz ortak bir oluşturucusu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="899a5-109">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="899a5-110">Yalnızca ortak özellikler ve alanların serisi kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="899a5-110">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="899a5-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="899a5-111">Robust Programming</span></span>  

 <span data-ttu-id="899a5-112">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="899a5-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="899a5-113">Seri hale getirilen sınıfın ortak, parametresiz bir oluşturucusu yok.</span><span class="sxs-lookup"><span data-stu-id="899a5-113">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="899a5-114">Dosyadaki veriler, seri durumdan çıkarılacak sınıftan verileri temsil etmez.</span><span class="sxs-lookup"><span data-stu-id="899a5-114">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="899a5-115">Dosya yok ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="899a5-115">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="899a5-116">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="899a5-116">.NET Framework Security</span></span>  

 <span data-ttu-id="899a5-117">Girişleri her zaman doğrulayın ve güvenilmeyen bir kaynaktaki verileri hiçbir zaman serisini kaldırma.</span><span class="sxs-lookup"><span data-stu-id="899a5-117">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="899a5-118">Yeniden oluşturulan nesne, yerel bir bilgisayarda, serisi kaldırılan kodun izinleriyle çalışır.</span><span class="sxs-lookup"><span data-stu-id="899a5-118">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="899a5-119">Verileri uygulamanızda kullanmadan önce tüm girişleri doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="899a5-119">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="899a5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="899a5-120">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="899a5-121">Nasıl yapılır: nesne verilerini bir XML dosyasına yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="899a5-121">How to: Write Object Data to an XML File (Visual Basic)</span></span>](how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="899a5-122">Serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="899a5-122">Serialization (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="899a5-123">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="899a5-123">Visual Basic Programming Guide</span></span>](../../index.md)
