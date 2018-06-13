---
title: Stil sayfası parametreleri ve uzantı nesneleri için XsltArgumentList
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: de2f0dce-6b98-4908-bba7-ed150cc50355
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 808d21ae0eabdc7502ef97facc3d45f2220883af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576815"
---
# <a name="xsltargumentlist-for-style-sheet-parameters-and-extension-objects"></a><span data-ttu-id="38cd8-102">Stil sayfası parametreleri ve uzantı nesneleri için XsltArgumentList</span><span class="sxs-lookup"><span data-stu-id="38cd8-102">XsltArgumentList for Style Sheet Parameters and Extension Objects</span></span>
<span data-ttu-id="38cd8-103"><xref:System.Xml.Xsl.XsltArgumentList> Sınıfı Dönüşümleri (XSLT) parametreleri ve XSLT uzantısı nesneleri için Genişletilebilir Stil sayfası dili içerir.</span><span class="sxs-lookup"><span data-stu-id="38cd8-103">The <xref:System.Xml.Xsl.XsltArgumentList> class contains Extensible Stylesheet Language for Transformations (XSLT) parameters and XSLT extension objects.</span></span> <span data-ttu-id="38cd8-104">İçine geçirildiğinde <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi, bu parametreler ve uzantı nesneleri stil sayfalarını çağrılan.</span><span class="sxs-lookup"><span data-stu-id="38cd8-104">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38cd8-105"><xref:System.Xml.Xsl.XslTransform> Ve <xref:System.Xml.Xsl.XsltArgumentList> sınıfları ' te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="38cd8-105">The <xref:System.Xml.Xsl.XslTransform> and <xref:System.Xml.Xsl.XsltArgumentList> classes are obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="38cd8-106">Kullanarak XSLT dönüştürmeleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="38cd8-106">You can perform XSLT transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="38cd8-107">Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="38cd8-107">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="38cd8-108"><xref:System.Xml.Xsl.XsltArgumentList> Sınıfı XSLT parametreleri ve XSLT uzantısı nesneleri içerir.</span><span class="sxs-lookup"><span data-stu-id="38cd8-108">The <xref:System.Xml.Xsl.XsltArgumentList> class contains XSLT parameters and XSLT extension objects.</span></span> <span data-ttu-id="38cd8-109">İçine geçirildiğinde <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi, bu parametreler ve uzantı nesneleri stil sayfalarını çağrılan.</span><span class="sxs-lookup"><span data-stu-id="38cd8-109">When passed into the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, these parameters and extension objects can be invoked from style sheets.</span></span>  
  
 <span data-ttu-id="38cd8-110">Katıştırılmış bir komut dosyası kullanarak yerine bir nesne geçirme avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="38cd8-110">The following are advantages to passing an object rather than using an embedded script:</span></span>  
  
-   <span data-ttu-id="38cd8-111">Daha iyi kapsülleme ve sınıfları kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="38cd8-111">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="38cd8-112">Stil sayfaları, küçük ve daha rahat olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="38cd8-112">Allows style sheets to be smaller and more maintainable.</span></span>  
  
-   <span data-ttu-id="38cd8-113">Ad alanları kümesi içinde tanımlanan dışında ait sınıfları yöntemleri çağırma destekler desteklenen <xref:System> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="38cd8-113">Supports calling methods on classes belonging to namespaces other than those defined within the set of supported <xref:System> namespaces.</span></span>  
  
-   <span data-ttu-id="38cd8-114">Sonuç ağaç parçaları kullanarak stil sayfası geçirilmesi destekler <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="38cd8-114">Supports passing result tree fragments to the style sheet with the use of the <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
## <a name="xslt-style-sheet-parameters"></a><span data-ttu-id="38cd8-115">XSLT stil sayfası parametreleri</span><span class="sxs-lookup"><span data-stu-id="38cd8-115">XSLT Style Sheet Parameters</span></span>  
 <span data-ttu-id="38cd8-116">XSLT parametreleri eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="38cd8-116">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="38cd8-117">Bir tam adı ve ad alanı Tekdüzen Kaynak Tanımlayıcısı (URI) o anda parametre nesnesi ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="38cd8-117">A qualified name and namespace Uniform Resource Identifier (URI) are associated with the parameter object at that time.</span></span>  
  
 <span data-ttu-id="38cd8-118">Parametre nesnesi, World Wide Web Konsorsiyumu (W3C) türüne karşılık gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="38cd8-118">The parameter object should correspond to a World Wide Web Consortium (W3C) type.</span></span> <span data-ttu-id="38cd8-119">Aşağıdaki tabloda, karşılık gelen W3C türleri eşdeğer gösterilmektedir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sınıfları (tür) ve W3C türü bir XML Path dili (XPath) türü veya XSLT türü olup.</span><span class="sxs-lookup"><span data-stu-id="38cd8-119">The following table shows the corresponding W3C types, the equivalent [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] classes (type), and whether the W3C type is an XML Path Language (XPath) type or XSLT type.</span></span>  
  
|<span data-ttu-id="38cd8-120">W3C türü</span><span class="sxs-lookup"><span data-stu-id="38cd8-120">W3C Type</span></span>|<span data-ttu-id="38cd8-121">Eşdeğer .NET Framework sınıf (tür)</span><span class="sxs-lookup"><span data-stu-id="38cd8-121">Equivalent .NET Framework class (type)</span></span>|<span data-ttu-id="38cd8-122">XPath türü veya XSLT türü</span><span class="sxs-lookup"><span data-stu-id="38cd8-122">XPath type or XSLT type</span></span>|  
|--------------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="38cd8-123">Dize</span><span class="sxs-lookup"><span data-stu-id="38cd8-123">String</span></span>|<span data-ttu-id="38cd8-124">System.String</span><span class="sxs-lookup"><span data-stu-id="38cd8-124">System.String</span></span>|<span data-ttu-id="38cd8-125">XPath</span><span class="sxs-lookup"><span data-stu-id="38cd8-125">XPath</span></span>|  
|<span data-ttu-id="38cd8-126">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="38cd8-126">Boolean</span></span>|<span data-ttu-id="38cd8-127">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="38cd8-127">System.Boolean</span></span>|<span data-ttu-id="38cd8-128">XPath</span><span class="sxs-lookup"><span data-stu-id="38cd8-128">XPath</span></span>|  
|<span data-ttu-id="38cd8-129">Sayı</span><span class="sxs-lookup"><span data-stu-id="38cd8-129">Number</span></span>|<span data-ttu-id="38cd8-130">System.Double</span><span class="sxs-lookup"><span data-stu-id="38cd8-130">System.Double</span></span>|<span data-ttu-id="38cd8-131">XPath</span><span class="sxs-lookup"><span data-stu-id="38cd8-131">XPath</span></span>|  
|<span data-ttu-id="38cd8-132">Sonuç ağacı parçası</span><span class="sxs-lookup"><span data-stu-id="38cd8-132">Result Tree Fragment</span></span>|<span data-ttu-id="38cd8-133">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="38cd8-133">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="38cd8-134">XSLT</span><span class="sxs-lookup"><span data-stu-id="38cd8-134">XSLT</span></span>|  
|<span data-ttu-id="38cd8-135">Düğüm kümesi</span><span class="sxs-lookup"><span data-stu-id="38cd8-135">Node Set</span></span>|<span data-ttu-id="38cd8-136">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="38cd8-136">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="38cd8-137">XPath</span><span class="sxs-lookup"><span data-stu-id="38cd8-137">XPath</span></span>|  
  
 <span data-ttu-id="38cd8-138">Parametre nesnesi yukarıdaki sınıflarından biri değilse, bunu çift veya dize için uygun şekilde zorlanır.</span><span class="sxs-lookup"><span data-stu-id="38cd8-138">If the parameter object is not one of the above classes, it is forced to either a Double or String, as appropriate.</span></span> <span data-ttu-id="38cd8-139">Int16, UInt16, Int32, UInt32, Int64, UInt64, tek ve ondalık türleri için bir çift zorlanır.</span><span class="sxs-lookup"><span data-stu-id="38cd8-139">Int16, UInt16, Int32, UInt32, Int64, UInt64, Single and Decimal types are forced to a Double.</span></span> <span data-ttu-id="38cd8-140">Tüm diğer türleri bir dizeye zorlanır kullanarak `ToString` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="38cd8-140">All other types are forced to a String using the `ToString` method.</span></span>  
  
#### <a name="to-use-the-xslt-parameter-the-user-needs-to-do-the-following"></a><span data-ttu-id="38cd8-141">XSLT parametre kullanmak üzere kullanıcı aşağıdakileri yapmalıdır:</span><span class="sxs-lookup"><span data-stu-id="38cd8-141">To use the XSLT parameter, the user needs to do the following:</span></span>  
  
1.  <span data-ttu-id="38cd8-142">Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> ve kullanarak nesneleri eklemek <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span><span class="sxs-lookup"><span data-stu-id="38cd8-142">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the objects using <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.</span></span>  
  
2.  <span data-ttu-id="38cd8-143">Parametreleri stil sayfası içinden çağırın.</span><span class="sxs-lookup"><span data-stu-id="38cd8-143">Call the parameters from the style sheet.</span></span>  
  
3.  <span data-ttu-id="38cd8-144">Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> için <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="38cd8-144">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="38cd8-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="38cd8-145">Example</span></span>  
 <span data-ttu-id="38cd8-146">Aşağıdaki örnek kullanır <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> hesaplanan iskonto tarih tutmak için bir parametre oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="38cd8-146">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold a calculated discount date.</span></span> <span data-ttu-id="38cd8-147">İndirim tarih sırası 20 gün olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="38cd8-147">The discount date is calculated to be 20 days from the order date.</span></span>  
  
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
  
### <a name="input"></a><span data-ttu-id="38cd8-148">Giriş</span><span class="sxs-lookup"><span data-stu-id="38cd8-148">Input</span></span>  
 <span data-ttu-id="38cd8-149">Order.XML</span><span class="sxs-lookup"><span data-stu-id="38cd8-149">order.xml</span></span>  
  
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
  
 <span data-ttu-id="38cd8-150">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="38cd8-150">discount.xsl</span></span>  
  
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
  
### <a name="output"></a><span data-ttu-id="38cd8-151">Çıkış</span><span class="sxs-lookup"><span data-stu-id="38cd8-151">Output</span></span>  
  
```xml  
<order>  
   <total>36.9</total>   
   15% discount if paid by: 5/6/2001 5:01:15 PM   
</order>  
```  
  
## <a name="xslt-extension-objects"></a><span data-ttu-id="38cd8-152">XSLT uzantısı nesneleri</span><span class="sxs-lookup"><span data-stu-id="38cd8-152">XSLT Extension Objects</span></span>  
 <span data-ttu-id="38cd8-153">XSLT uzantısı nesnelerinin eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="38cd8-153">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="38cd8-154">Bir tam adı ve ad alanı URI'si o anda uzantısı nesne ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="38cd8-154">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
 <span data-ttu-id="38cd8-155">Bir nesne eklendiğinde, çağıranın <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> güvenlik ilkesinde tam olarak güvenilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="38cd8-155">When an object is added, the caller of the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> must be fully trusted in the security policy.</span></span> <span data-ttu-id="38cd8-156">Arayan yarı güvenilmiyorsa eklenmesi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="38cd8-156">If the caller is semi-trusted, the addition will fail.</span></span>  
  
 <span data-ttu-id="38cd8-157">Bir nesne başarıyla eklendi ancak, yürütme başarılı olacağını garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="38cd8-157">Though an object is added successfully, it does not guarantee that the execution will be successful.</span></span> <span data-ttu-id="38cd8-158">Zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çağrıldığında, izin verilen bulgu göre hesaplanır <xref:System.Xml.Xsl.XslTransform.Load%2A> zaman ve izin kümesi için tüm dönüştürme süreci atanır.</span><span class="sxs-lookup"><span data-stu-id="38cd8-158">When the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is called, permissions are calculated against the evidence provided at <xref:System.Xml.Xsl.XslTransform.Load%2A> time, and that permission set is assigned to the entire transformation process.</span></span> <span data-ttu-id="38cd8-159">Uzantı nesnesi kümesinde bulunamadı izinleri gerektiren bir eylem başlatmak çalışırsa, bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="38cd8-159">If an extension object attempts to initiate an action that requires permissions not found in the set, an exception is thrown.</span></span>  
  
 <span data-ttu-id="38cd8-160">Uzantı nesnelerden döndürülen veri türleri dört temel XPath veri türlerinin sayısı, dize, Boolean ve düğüm kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="38cd8-160">The data types returned from extension objects are one of the four basic XPath data types of number, string, Boolean, and node set.</span></span>  
  
#### <a name="to-use-the-xslt-extension-object-the-user-needs-to-do-the-following"></a><span data-ttu-id="38cd8-161">XSLT uzantı nesnesi kullanmak için kullanıcı aşağıdakileri yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="38cd8-161">To use the XSLT extension object, the user needs to do the following:</span></span>  
  
1.  <span data-ttu-id="38cd8-162">Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> ve uzantı nesnesini kullanarak eklemek <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="38cd8-162">Create an <xref:System.Xml.Xsl.XsltArgumentList> and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.</span></span>  
  
2.  <span data-ttu-id="38cd8-163">Stil sayfası uzantısı nesnesinden çağırır.</span><span class="sxs-lookup"><span data-stu-id="38cd8-163">Invoke the extension object from the style sheet.</span></span>  
  
3.  <span data-ttu-id="38cd8-164">Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> için <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="38cd8-164">Pass the <xref:System.Xml.Xsl.XsltArgumentList> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span>  
  
### <a name="example"></a><span data-ttu-id="38cd8-165">Örnek</span><span class="sxs-lookup"><span data-stu-id="38cd8-165">Example</span></span>  
 <span data-ttu-id="38cd8-166">Aşağıdaki örnek, RADIUS verilen dairenin çevresi hesaplar.</span><span class="sxs-lookup"><span data-stu-id="38cd8-166">The following example calculates the circumference of a circle given its radius.</span></span>  
  
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
  public class Calculate{  
  
    private double circ = 0;  
  
    public double Circumference(double radius){  
       circ = Math.PI*2*radius;  
       return circ;  
    }  
  }  
}  
```  
  
### <a name="input"></a><span data-ttu-id="38cd8-167">Giriş</span><span class="sxs-lookup"><span data-stu-id="38cd8-167">Input</span></span>  
 <span data-ttu-id="38cd8-168">Number.XML</span><span class="sxs-lookup"><span data-stu-id="38cd8-168">number.xml</span></span>  
  
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
  
 <span data-ttu-id="38cd8-169">Circle.xsl</span><span class="sxs-lookup"><span data-stu-id="38cd8-169">circle.xsl</span></span>  
  
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
  
### <a name="output"></a><span data-ttu-id="38cd8-170">Çıkış</span><span class="sxs-lookup"><span data-stu-id="38cd8-170">Output</span></span>  
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
  
## <a name="see-also"></a><span data-ttu-id="38cd8-171">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38cd8-171">See Also</span></span>  
 [<span data-ttu-id="38cd8-172">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="38cd8-172">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
