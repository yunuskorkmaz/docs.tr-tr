---
title: 'Nasıl yapılır: XslTransform Kodunuzu Geçirme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
ms.openlocfilehash: 42ca884c269611ebf7dae3b4e7aa8a39ba96b521
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287746"
---
# <a name="how-to-migrate-your-xsltransform-code"></a><span data-ttu-id="1bc00-102">Nasıl yapılır: XslTransform Kodunuzu Geçirme</span><span class="sxs-lookup"><span data-stu-id="1bc00-102">How to: Migrate Your XslTransform Code</span></span>
<span data-ttu-id="1bc00-103">Yeni XSLT sınıfları, mevcut sınıflara çok benzer olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1bc00-103">The new XSLT classes have been designed to be very similar to the existing classes.</span></span> <span data-ttu-id="1bc00-104"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, sınıfının yerini alır <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-104">The <xref:System.Xml.Xsl.XslCompiledTransform> class replaces the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="1bc00-105">Stil sayfaları yöntemi kullanılarak derlenir <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-105">Style sheets are compiled using the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="1bc00-106">Dönüşümler yöntemi kullanılarak yürütülür <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-106">Transforms are executed using the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="1bc00-107">Aşağıdaki yordamlarda ortak XSLT görevleri gösterilmektedir ve sınıfı ile sınıf karşılaştırması kullanılarak kod karşılaştırılır <xref:System.Xml.Xsl.XslTransform> <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-107">The following procedures show common XSLT tasks, and compare the code using the <xref:System.Xml.Xsl.XslTransform> class versus the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a><span data-ttu-id="1bc00-108">Bir dosyayı ve çıktıyı bir URI 'ye dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="1bc00-108">To transform a file and output to a URI</span></span>  
  
- <span data-ttu-id="1bc00-109">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-109">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
- <span data-ttu-id="1bc00-110">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-110">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a><span data-ttu-id="1bc00-111">Bir stil sayfası derlemek ve varsayılan kimlik bilgileriyle çözümleyici kullanmak için</span><span class="sxs-lookup"><span data-stu-id="1bc00-111">To compile a style sheet and use a resolver with default credentials</span></span>  
  
- <span data-ttu-id="1bc00-112">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-112">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
- <span data-ttu-id="1bc00-113">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-113">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="1bc00-114">XSLT parametresi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="1bc00-114">To use an XSLT parameter</span></span>  
  
- <span data-ttu-id="1bc00-115">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-115">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
- <span data-ttu-id="1bc00-116">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-116">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a><span data-ttu-id="1bc00-117">XSLT komut dosyalarını etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="1bc00-117">To enable XSLT scripting</span></span>  
  
- <span data-ttu-id="1bc00-118">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-118">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
- <span data-ttu-id="1bc00-119">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-119">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a><span data-ttu-id="1bc00-120">Sonuçları DOM nesnesine yüklemek için</span><span class="sxs-lookup"><span data-stu-id="1bc00-120">To load the results into a DOM object</span></span>  
  
- <span data-ttu-id="1bc00-121">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-121">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
- <span data-ttu-id="1bc00-122">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-122">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1bc00-123"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfın, XSLT dönüştürme sonuçlarını nesne olarak döndüren bir yöntemi yoktur <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-123">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have a method that returns the XSLT transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="1bc00-124">Ancak, bir XML dosyasına çıktı verebilir ve XML dosyasını başka bir nesneye yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bc00-124">However, you can output to an XML file and load the XML file into another object.</span></span>  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a><span data-ttu-id="1bc00-125">Sonuçları başka bir veri deposuna akışa almak için</span><span class="sxs-lookup"><span data-stu-id="1bc00-125">To stream the results into another data store</span></span>  
  
- <span data-ttu-id="1bc00-126">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-126">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
- <span data-ttu-id="1bc00-127">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="1bc00-127">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a><span data-ttu-id="1bc00-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bc00-128">See also</span></span>

- [<span data-ttu-id="1bc00-129">XslTransform Sınıfından Geçirme</span><span class="sxs-lookup"><span data-stu-id="1bc00-129">Migrating From the XslTransform Class</span></span>](migrating-from-the-xsltransform-class.md)
- [<span data-ttu-id="1bc00-130">XslCompiledTransform Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="1bc00-130">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)
