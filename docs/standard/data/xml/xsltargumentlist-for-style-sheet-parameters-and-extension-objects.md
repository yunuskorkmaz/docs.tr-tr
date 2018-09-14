---
title: Stil sayfası parametreleri ve genişletme nesneleri için XsltArgumentList
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1fb973dcde1ca31a57fbc3022d3eb1c92a2a9d0f
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45507566"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a><span data-ttu-id="c113f-102">Stil sayfası parametreleri ve genişletme nesneleri için XsltArgumentList</span><span class="sxs-lookup"><span data-stu-id="c113f-102">XsltArgumentList for Style Sheet Parameters and Extension Objects</span></span>
<span data-ttu-id="c113f-103"><xref:System.Xml.Xsl.XsltArgumentList> Sınıfı içeren Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) parametreleri ve XSLT genişletme nesneleri için.</span><span class="sxs-lookup"><span data-stu-id="c113f-103">The <xref:System.Xml.Xsl.XsltArgumentList> class contains Extensible Stylesheet Language for Transformations (XSLT) parameters and XSLT extension objects.</span></span> <span data-ttu-id="c113f-104">Yöntemlere geçirilen zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi, bu parametreleri ve genişletme nesneleri stil sayfası içinden çağrılan.</span><span class="sxs-lookup"><span data-stu-id="c113f-104">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c113f-105"><xref:System.Xml.Xsl.XslTransform> Ve <xref:System.Xml.Xsl.XsltArgumentList> sınıflardır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c113f-105">The <xref:System.Xml.Xsl.XslTransform> and <xref:System.Xml.Xsl.XsltArgumentList> classes are obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="c113f-106">Kullanarak XSLT dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c113f-106">You can perform XSLT transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="c113f-107">Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="c113f-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="c113f-108"><xref:System.Xml.Xsl.XsltArgumentList> Sınıfı XSLT parametreleri ve XSLT genişletme nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c113f-108">The <xref:System.Xml.Xsl.XsltArgumentList> class contains XSLT parameters and XSLT extension objects.</span></span> <span data-ttu-id="c113f-109">Yöntemlere geçirilen zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi, bu parametreleri ve genişletme nesneleri stil sayfası içinden çağrılan.</span><span class="sxs-lookup"><span data-stu-id="c113f-109">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
 <span data-ttu-id="c113f-110">Katıştırılmış bir betik kullanmak yerine bir nesne geçirme avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c113f-110">The following are advantages to passing an object rather than using an embedded script:</span></span>  
  
-   <span data-ttu-id="c113f-111">Daha iyi kapsülleme ve sınıfları kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c113f-111">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="c113f-112">Stil sayfaları, daha küçük ve daha rahat olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c113f-112">Allows style sheets to be smaller and more maintainable.</span></span>  
  
-   <span data-ttu-id="c113f-113">Desteklenen dizi içinde tanımlanan dışındaki ad alanlarına ait sınıfların yöntemleri çağırma destekler <xref:System> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="c113f-113">Supports calling methods on classes belonging to namespaces other than those defined within the set of supported <xref:System> namespaces.</span></span>  
  
-   <span data-ttu-id="c113f-114">Sonucu ağacı parçalarını kullanımını ile stil sayfası geçirerek destekler <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="c113f-114">Supports passing result tree fragments to the style sheet with the use of the <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
## <a name="xslt-style-sheet-parameters"></a><span data-ttu-id="c113f-115">XSLT stil sayfası parametreleri</span><span class="sxs-lookup"><span data-stu-id="c113f-115">XSLT Style Sheet Parameters</span></span>  
 <span data-ttu-id="c113f-116">XSLT parametreleri eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c113f-116">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="c113f-117">Bir tam adı ve ad alanı Tekdüzen Kaynak Tanımlayıcısı (URI), o anda parametresi nesnesi ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="c113f-117">A qualified name and namespace Uniform Resource Identifier (URI) are associated with the parameter object at that time.</span></span>  
  
 <span data-ttu-id="c113f-118">Parametre nesnesine bir World Wide Web Consortium (W3C) türüne karşılık gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="c113f-118">The parameter object should correspond to a World Wide Web Consortium (W3C) type.</span></span> <span data-ttu-id="c113f-119">Aşağıdaki tabloda karşılık gelen W3C türleri, eşdeğer gösterir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sınıfları (tür) ve W3C türün bir XML yolu dil (XPath) türü veya XSLT türü olup.</span><span class="sxs-lookup"><span data-stu-id="c113f-119">The following table shows the corresponding W3C types, the equivalent [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] classes (type), and whether the W3C type is an XML Path Language (XPath) type or XSLT type.</span></span>  
  
|<span data-ttu-id="c113f-120">W3C türü</span><span class="sxs-lookup"><span data-stu-id="c113f-120">W3C Type</span></span>|<span data-ttu-id="c113f-121">Eşdeğeri .NET Framework sınıfı (tür)</span><span class="sxs-lookup"><span data-stu-id="c113f-121">Equivalent .NET Framework class (type)</span></span>|<span data-ttu-id="c113f-122">XPath türü veya XSLT türü</span><span class="sxs-lookup"><span data-stu-id="c113f-122">XPath type or XSLT type</span></span>|  
|--------------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="c113f-123">Dize</span><span class="sxs-lookup"><span data-stu-id="c113f-123">String</span></span>|<span data-ttu-id="c113f-124">System.String</span><span class="sxs-lookup"><span data-stu-id="c113f-124">System.String</span></span>|<span data-ttu-id="c113f-125">XPath</span><span class="sxs-lookup"><span data-stu-id="c113f-125">XPath</span></span>|  
|<span data-ttu-id="c113f-126">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="c113f-126">Boolean</span></span>|<span data-ttu-id="c113f-127">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="c113f-127">System.Boolean</span></span>|<span data-ttu-id="c113f-128">XPath</span><span class="sxs-lookup"><span data-stu-id="c113f-128">XPath</span></span>|  
|<span data-ttu-id="c113f-129">Sayı</span><span class="sxs-lookup"><span data-stu-id="c113f-129">Number</span></span>|<span data-ttu-id="c113f-130">System.Double</span><span class="sxs-lookup"><span data-stu-id="c113f-130">System.Double</span></span>|<span data-ttu-id="c113f-131">XPath</span><span class="sxs-lookup"><span data-stu-id="c113f-131">XPath</span></span>|  
|<span data-ttu-id="c113f-132">Sonuç ağacı parçası</span><span class="sxs-lookup"><span data-stu-id="c113f-132">Result Tree Fragment</span></span>|<span data-ttu-id="c113f-133">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="c113f-133">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="c113f-134">XSLT</span><span class="sxs-lookup"><span data-stu-id="c113f-134">XSLT</span></span>|  
|<span data-ttu-id="c113f-135">Düğüm kümesi</span><span class="sxs-lookup"><span data-stu-id="c113f-135">Node Set</span></span>|<span data-ttu-id="c113f-136">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="c113f-136">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="c113f-137">XPath</span><span class="sxs-lookup"><span data-stu-id="c113f-137">XPath</span></span>|  
  
 <span data-ttu-id="c113f-138">Parametre nesnesine yukarıdaki sınıflardan biri değilse, bunu Double veya dizesi için uygun şekilde zorlanır.</span><span class="sxs-lookup"><span data-stu-id="c113f-138">If the parameter object is not one of the above classes, it is forced to either a Double or String, as appropriate.</span></span> <span data-ttu-id="c113f-139">Int16, Uınt16, Int32, Uınt32, Int64, UInt64, tek ve ondalık türleri için bir Double zorlanır.</span><span class="sxs-lookup"><span data-stu-id="c113f-139">Int16, UInt16, Int32, UInt32, Int64, UInt64, Single and Decimal types are forced to a Double.</span></span> <span data-ttu-id="c113f-140">Diğer tüm türlerin bir dizeye zorlanır kullanarak `ToString` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c113f-140">All other types are forced to a String using the `ToString` method.</span></span>  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a><span data-ttu-id="c113f-141">XSLT parametresini kullanmak için kullanıcı şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="c113f-141">To use the XSLT parameter, the user needs to do the following:</span></span>  
  
1.  <span data-ttu-id="c113f-142">Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> ve kullanarak nesne eklemek <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span><span class="sxs-lookup"><span data-stu-id="c113f-142">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the objects using <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span></span>  
  
2.  <span data-ttu-id="c113f-143">Stil sayfası parametreleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="c113f-143">Call the parameters from the style sheet.</span></span>  
  
3.  <span data-ttu-id="c113f-144">Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> için <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c113f-144">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="c113f-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="c113f-145">Example</span></span>  
 <span data-ttu-id="c113f-146">Aşağıdaki örnekte <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi hesaplanan indirimi tarihini tutmak için bir parametre oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c113f-146">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold a calculated discount date.</span></span> <span data-ttu-id="c113f-147">İndirimi tarihini, sipariş tarihi 20 gün olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="c113f-147">The discount date is calculated to be 20 days from the order date.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public class Sample  
  
   Private Const filename As String = "order.xml"  
   Private Const stylesheet As String = "discount.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Calculate the discount date.  
    Dim today As DateTime = DateTime.Now  
    Dim d As DateTime = today.AddDays(20)  
    xslArg.AddParam("discount", "", d.ToString())  
  
    'Create an XmlTextWriter to handle the output.  
    Dim writer As XmlTextWriter = New XmlTextWriter("orderout.xml", Nothing)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
  
    writer.Close()  
  
  End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "order.xml";  
   private const String stylesheet = "discount.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Calculate the discount date.  
    DateTime today = DateTime.Now;  
    DateTime d = today.AddDays(20);  
    xslArg.AddParam("discount", "", d.ToString());  
  
    //Create an XmlTextWriter to handle the output.  
    XmlTextWriter writer = new XmlTextWriter("orderout.xml", null);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="c113f-148">Giriş</span><span class="sxs-lookup"><span data-stu-id="c113f-148">Input</span></span>  
 <span data-ttu-id="c113f-149">Order.XML</span><span class="sxs-lookup"><span data-stu-id="c113f-149">order.xml</span></span>  
  
```xml  
<!--Represents a customer order-->  
<order>  
  <book ISBN='10-861003-324'>  
    <title>The Handmaid's Tale</title>  
    <price>19.95</price>  
  </book>  
  <cd ISBN='2-3631-4'>  
    <title>Americana</title>  
    <price>16.95</price>  
  </cd>  
</order>  
```  
  
 <span data-ttu-id="c113f-150">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="c113f-150">discount.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:param name="discount"/>  
  <xsl:template match="/">  
    <order>  
      <xsl:variable name="sub-total" select="sum(//price)"/>  
      <total><xsl:value-of select="$sub-total"/></total>  
      15% discount if paid by: <xsl:value-of select="$discount"/>  
    </order>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a><span data-ttu-id="c113f-151">Çıkış</span><span class="sxs-lookup"><span data-stu-id="c113f-151">Output</span></span>  
  
```xml  
<order>  
   <total>36.9</total>   
   15% discount if paid by: 5/6/2001 5:01:15 PM   
</order>  
```  
  
## <a name="xslt-extension-objects"></a><span data-ttu-id="c113f-152">XSLT genişletme nesneleri</span><span class="sxs-lookup"><span data-stu-id="c113f-152">XSLT Extension Objects</span></span>  
 <span data-ttu-id="c113f-153">XSLT genişletme nesneleri eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c113f-153">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="c113f-154">Bir tam adı ve ad alanı URI o anda uzantısı nesnesi ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="c113f-154">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
 <span data-ttu-id="c113f-155">Bir nesne eklendiğinde, çağıran <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> güvenlik ilkesinde tam olarak güvenilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c113f-155">When an object is added, the caller of the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> must be fully trusted in the security policy.</span></span> <span data-ttu-id="c113f-156">Çağıranın kısmen güvenilen ise, ayrıca başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c113f-156">If the caller is semi-trusted, the addition will fail.</span></span>  
  
 <span data-ttu-id="c113f-157">Nesne başarıyla eklendi ancak bunu yürütme başarılı olacağını garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="c113f-157">Though an object is added successfully, it does not guarantee that the execution will be successful.</span></span> <span data-ttu-id="c113f-158">Zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çağrıldığında, izin verilen kanıt karşı hesaplandığı <xref:System.Xml.Xsl.XslTransform.Load%2A> zaman ve izin kümesi için tüm dönüştürme süreci atanır.</span><span class="sxs-lookup"><span data-stu-id="c113f-158">When the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is called, permissions are calculated against the evidence provided at <xref:System.Xml.Xsl.XslTransform.Load%2A> time, and that permission set is assigned to the entire transformation process.</span></span> <span data-ttu-id="c113f-159">Kümede bulunamadı izinleri gerektiren bir eylem başlatmak bir uzantı nesnesi çalışırsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c113f-159">If an extension object attempts to initiate an action that requires permissions not found in the set, an exception is thrown.</span></span>  
  
 <span data-ttu-id="c113f-160">Uzantı nesnelerinden döndürülen veri türleri, sayı, dize, Boolean ve düğüm kümesinin dört temel XPath veri türleri biridir.</span><span class="sxs-lookup"><span data-stu-id="c113f-160">The data types returned from extension objects are one of the four basic XPath data types of number, string, Boolean, and node set.</span></span>  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a><span data-ttu-id="c113f-161">XSLT uzantı nesnesini kullanmak için kullanıcı aşağıdakileri yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="c113f-161">To use the XSLT extension object, the user needs to do the following:</span></span>  
  
1.  <span data-ttu-id="c113f-162">Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> ve uzantısını kullanarak nesne eklemek <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="c113f-162">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span></span>  
  
2.  <span data-ttu-id="c113f-163">Stil sayfası uzantısı nesneden çağırın.</span><span class="sxs-lookup"><span data-stu-id="c113f-163">Invoke the extension object from the style sheet.</span></span>  
  
3.  <span data-ttu-id="c113f-164">Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> için <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c113f-164">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="c113f-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="c113f-165">Example</span></span>  
 <span data-ttu-id="c113f-166">Aşağıdaki örnek, RADIUS verilmiş bir daire çevresi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="c113f-166">The following example calculates the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "circle.xsl"  
  
   Public Shared Sub Main()  
        Dim test As Sample = New Sample  
   End Sub  
  
  Public Sub New()  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XsltArgumentList.  
    Dim xslArg As XsltArgumentList = New XsltArgumentList  
  
    'Add an object to calculate the circumference of the circle.  
    Dim obj As Calculate = New Calculate  
    xslArg.AddExtensionObject("urn:myObj", obj)  
  
    'Create an XmlTextWriter to output to the console.  
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
  
    'Transform the file.  
    xslt.Transform(doc, xslArg, writer, Nothing)  
    writer.Close()  
  
  End Sub  
  
  'Calculates the circumference of a circle given the radius.  
  Public Class Calculate  
  
    Private circ As double = 0  
  
    Public Function Circumference(radius As Double) As Double  
       circ = Math.PI*2*radius  
       Return circ  
    End Function  
  End Class  
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "circle.xsl";  
  
   public static void Main() {  
  
        Sample test = new Sample();  
    }  
  
  public Sample() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XsltArgumentList.  
    XsltArgumentList xslArg = new XsltArgumentList();  
  
    //Add an object to calculate the circumference of the circle.  
    Calculate obj = new Calculate();  
    xslArg.AddExtensionObject("urn:myObj", obj);  
  
    //Create an XmlTextWriter to output to the console.  
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
  
    //Transform the file.  
    xslt.Transform(doc, xslArg, writer, null);  
    writer.Close();  
  
  }  
  
  //Calculates the circumference of a circle given the radius.  
  public class Calculate {  
  
    private double circ = 0;  
  
    public double Circumference(double radius){  
       circ = Math.PI*2*radius;  
       return circ;  
    }  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="c113f-167">Giriş</span><span class="sxs-lookup"><span data-stu-id="c113f-167">Input</span></span>  
 <span data-ttu-id="c113f-168">Number.XML</span><span class="sxs-lookup"><span data-stu-id="c113f-168">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>    
```  
  
 <span data-ttu-id="c113f-169">Circle.xsl</span><span class="sxs-lookup"><span data-stu-id="c113f-169">circle.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:myObj="urn:myObj">  
  
  <xsl:template match="data">  
  <circles>  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="myObj:Circumference(radius)"/>          
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="output"></a><span data-ttu-id="c113f-170">Çıkış</span><span class="sxs-lookup"><span data-stu-id="c113f-170">Output</span></span>  
 `<circles xmlns:myObj="urn:myObj">`  
  
 `<circle>`  
  
 `<radius>12</radius>`  
  
 `<circumference>75.398223686155</circumference>`  
  
 `</circle>`  
  
 `<circle>`  
  
 `<radius>37.5</radius>`  
  
 `<circumference>235.61944901923448</circumference>`  
  
 `</circle>`  
  
 `</circles>`  
  
## <a name="see-also"></a><span data-ttu-id="c113f-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c113f-171">See also</span></span>

- [<span data-ttu-id="c113f-172">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="c113f-172">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
