---
title: 'Nasıl yapılır: XslTransform kodunuzu geçirme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
ms.openlocfilehash: 2bc5cbc1b0857a82d3b0a11f05a4eb5756724546
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710849"
---
# <a name="how-to-migrate-your-xsltransform-code"></a><span data-ttu-id="f65b3-102">Nasıl yapılır: XslTransform kodunuzu geçirme</span><span class="sxs-lookup"><span data-stu-id="f65b3-102">How to: Migrate Your XslTransform Code</span></span>
<span data-ttu-id="f65b3-103">Yeni XSLT sınıfları, mevcut sınıflara çok benzer olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f65b3-103">The new XSLT classes have been designed to be very similar to the existing classes.</span></span> <span data-ttu-id="f65b3-104"><xref:System.Xml.Xsl.XslCompiledTransform> sınıfı <xref:System.Xml.Xsl.XslTransform> sınıfının yerini alır.</span><span class="sxs-lookup"><span data-stu-id="f65b3-104">The <xref:System.Xml.Xsl.XslCompiledTransform> class replaces the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="f65b3-105">Stil sayfaları <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi kullanılarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="f65b3-105">Style sheets are compiled using the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="f65b3-106">Dönüşümler <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi kullanılarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="f65b3-106">Transforms are executed using the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="f65b3-107">Aşağıdaki yordamlarda ortak XSLT görevleri gösterilmektedir ve <xref:System.Xml.Xsl.XslTransform> sınıfını kullanarak kodu <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="f65b3-107">The following procedures show common XSLT tasks, and compare the code using the <xref:System.Xml.Xsl.XslTransform> class versus the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a><span data-ttu-id="f65b3-108">Bir dosyayı ve çıktıyı bir URI 'ye dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="f65b3-108">To transform a file and output to a URI</span></span>  
  
- <span data-ttu-id="f65b3-109"><xref:System.Xml.Xsl.XslTransform> sınıfını kullanan kod.</span><span class="sxs-lookup"><span data-stu-id="f65b3-109">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
- <span data-ttu-id="f65b3-110"><xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanan kod.</span><span class="sxs-lookup"><span data-stu-id="f65b3-110">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a><span data-ttu-id="f65b3-111">Bir stil sayfası derlemek ve varsayılan kimlik bilgileriyle çözümleyici kullanmak için</span><span class="sxs-lookup"><span data-stu-id="f65b3-111">To compile a style sheet and use a resolver with default credentials</span></span>  
  
- <span data-ttu-id="f65b3-112"><xref:System.Xml.Xsl.XslTransform> sınıfını kullanan kod.</span><span class="sxs-lookup"><span data-stu-id="f65b3-112">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
- <span data-ttu-id="f65b3-113"><xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanan kod.</span><span class="sxs-lookup"><span data-stu-id="f65b3-113">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="f65b3-114">XSLT parametresi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="f65b3-114">To use an XSLT parameter</span></span>  
  
- <span data-ttu-id="f65b3-115"><xref:System.Xml.Xsl.XslTransform> sınıfını kullanan kod.</span><span class="sxs-lookup"><span data-stu-id="f65b3-115">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
- <span data-ttu-id="f65b3-116"><xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanan kod.</span><span class="sxs-lookup"><span data-stu-id="f65b3-116">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a><span data-ttu-id="f65b3-117">XSLT komut dosyalarını etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="f65b3-117">To enable XSLT scripting</span></span>  
  
- <span data-ttu-id="f65b3-118"><xref:System.Xml.Xsl.XslTransform> sınıfını kullanan kod.</span><span class="sxs-lookup"><span data-stu-id="f65b3-118">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
- <span data-ttu-id="f65b3-119"><xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanan kod.</span><span class="sxs-lookup"><span data-stu-id="f65b3-119">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a><span data-ttu-id="f65b3-120">Sonuçları DOM nesnesine yüklemek için</span><span class="sxs-lookup"><span data-stu-id="f65b3-120">To load the results into a DOM object</span></span>  
  
- <span data-ttu-id="f65b3-121"><xref:System.Xml.Xsl.XslTransform> sınıfını kullanan kod.</span><span class="sxs-lookup"><span data-stu-id="f65b3-121">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
- <span data-ttu-id="f65b3-122"><xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanan kod.</span><span class="sxs-lookup"><span data-stu-id="f65b3-122">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f65b3-123"><xref:System.Xml.Xsl.XslCompiledTransform> sınıfı, XSLT dönüştürme sonuçlarını bir <xref:System.Xml.XmlReader> nesnesi olarak döndüren bir yönteme sahip değil.</span><span class="sxs-lookup"><span data-stu-id="f65b3-123">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have a method that returns the XSLT transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="f65b3-124">Ancak, bir XML dosyasına çıktı verebilir ve XML dosyasını başka bir nesneye yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f65b3-124">However, you can output to an XML file and load the XML file into another object.</span></span>  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a><span data-ttu-id="f65b3-125">Sonuçları başka bir veri deposuna akışa almak için</span><span class="sxs-lookup"><span data-stu-id="f65b3-125">To stream the results into another data store</span></span>  
  
- <span data-ttu-id="f65b3-126"><xref:System.Xml.Xsl.XslTransform> sınıfını kullanan kod.</span><span class="sxs-lookup"><span data-stu-id="f65b3-126">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
- <span data-ttu-id="f65b3-127"><xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanan kod.</span><span class="sxs-lookup"><span data-stu-id="f65b3-127">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a><span data-ttu-id="f65b3-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f65b3-128">See also</span></span>

- [<span data-ttu-id="f65b3-129">XslTransform Sınıfından Geçirme</span><span class="sxs-lookup"><span data-stu-id="f65b3-129">Migrating From the XslTransform Class</span></span>](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)
- [<span data-ttu-id="f65b3-130">XslCompiledTransform Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="f65b3-130">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
