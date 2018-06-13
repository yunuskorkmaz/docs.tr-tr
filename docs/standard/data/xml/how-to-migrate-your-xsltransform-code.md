---
title: 'Nasıl yapılır: çok kodunuzu geçirme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fcfe8b0fbbc829c1bee08b761271f4d12b6ae05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571009"
---
# <a name="how-to-migrate-your-xsltransform-code"></a><span data-ttu-id="6cafa-102">Nasıl yapılır: çok kodunuzu geçirme</span><span class="sxs-lookup"><span data-stu-id="6cafa-102">How to: Migrate Your XslTransform Code</span></span>
<span data-ttu-id="6cafa-103">Yeni XSLT sınıfları varolan sınıfları çok benzer şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6cafa-103">The new XSLT classes have been designed to be very similar to the existing classes.</span></span> <span data-ttu-id="6cafa-104"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıf değiştirir <xref:System.Xml.Xsl.XslTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cafa-104">The <xref:System.Xml.Xsl.XslCompiledTransform> class replaces the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="6cafa-105">Stil sayfaları, kullanarak derlenen <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6cafa-105">Style sheets are compiled using the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="6cafa-106">Dönüşümler kullanarak yürütülme <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6cafa-106">Transforms are executed using the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="6cafa-107">Aşağıdaki yordamlar ortak XSLT görevleri göster ve kod kullanarak karşılaştırın <xref:System.Xml.Xsl.XslTransform> karşı sınıfı <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cafa-107">The following procedures show common XSLT tasks, and compare the code using the <xref:System.Xml.Xsl.XslTransform> class versus the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a><span data-ttu-id="6cafa-108">Dosya ve bir URI çıktısına dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="6cafa-108">To transform a file and output to a URI</span></span>  
  
-   <span data-ttu-id="6cafa-109">Kullanarak kod <xref:System.Xml.Xsl.XslTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cafa-109">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
-   <span data-ttu-id="6cafa-110">Kullanarak kod <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cafa-110">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a><span data-ttu-id="6cafa-111">Stil sayfası derlemek ve çözümleyici varsayılan kimlik bilgileri ile kullanmak için</span><span class="sxs-lookup"><span data-stu-id="6cafa-111">To compile a style sheet and use a resolver with default credentials</span></span>  
  
-   <span data-ttu-id="6cafa-112">Kullanarak kod <xref:System.Xml.Xsl.XslTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cafa-112">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
-   <span data-ttu-id="6cafa-113">Kullanarak kod <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cafa-113">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="6cafa-114">XSLT parametresini kullanma</span><span class="sxs-lookup"><span data-stu-id="6cafa-114">To use an XSLT parameter</span></span>  
  
-   <span data-ttu-id="6cafa-115">Kullanarak kod <xref:System.Xml.Xsl.XslTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cafa-115">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
-   <span data-ttu-id="6cafa-116">Kullanarak kod <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cafa-116">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a><span data-ttu-id="6cafa-117">XSLT betik kullanımını etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="6cafa-117">To enable XSLT scripting</span></span>  
  
-   <span data-ttu-id="6cafa-118">Kullanarak kod <xref:System.Xml.Xsl.XslTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cafa-118">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
-   <span data-ttu-id="6cafa-119">Kullanarak kod <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cafa-119">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a><span data-ttu-id="6cafa-120">Sonuçları bir DOM nesnesine yüklemek için</span><span class="sxs-lookup"><span data-stu-id="6cafa-120">To load the results into a DOM object</span></span>  
  
-   <span data-ttu-id="6cafa-121">Kullanarak kod <xref:System.Xml.Xsl.XslTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cafa-121">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
-   <span data-ttu-id="6cafa-122">Kullanarak kod <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cafa-122">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6cafa-123"><xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı olarak XSLT dönüşümü sonuçları döndüren bir yöntem yok bir <xref:System.Xml.XmlReader> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="6cafa-123">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have a method that returns the XSLT transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="6cafa-124">Ancak, bir XML dosyasına çıkarmak ve başka bir nesnede XML dosyasını yükle.</span><span class="sxs-lookup"><span data-stu-id="6cafa-124">However, you can output to an XML file and load the XML file into another object.</span></span>  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a><span data-ttu-id="6cafa-125">Başka bir veri deposuna sonuçları akışı</span><span class="sxs-lookup"><span data-stu-id="6cafa-125">To stream the results into another data store</span></span>  
  
-   <span data-ttu-id="6cafa-126">Kullanarak kod <xref:System.Xml.Xsl.XslTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cafa-126">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
-   <span data-ttu-id="6cafa-127">Kullanarak kod <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6cafa-127">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a><span data-ttu-id="6cafa-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6cafa-128">See Also</span></span>  
 [<span data-ttu-id="6cafa-129">XslTransform Sınıfından Geçirme</span><span class="sxs-lookup"><span data-stu-id="6cafa-129">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 [<span data-ttu-id="6cafa-130">XslCompiledTransform Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="6cafa-130">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
