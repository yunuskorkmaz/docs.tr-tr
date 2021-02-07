---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: XslTransform kodunuzu geçirme'
title: 'Nasıl yapılır: XslTransform Kodunuzu Geçirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 910beb2f-cfb3-4e8e-9936-f7e0c5f4064a
ms.openlocfilehash: d8a05f98df70009750f59c53a760f9da698dd38e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713890"
---
# <a name="how-to-migrate-your-xsltransform-code"></a><span data-ttu-id="10c7c-103">Nasıl yapılır: XslTransform Kodunuzu Geçirme</span><span class="sxs-lookup"><span data-stu-id="10c7c-103">How to: Migrate Your XslTransform Code</span></span>

<span data-ttu-id="10c7c-104">Yeni XSLT sınıfları, mevcut sınıflara çok benzer olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="10c7c-104">The new XSLT classes have been designed to be very similar to the existing classes.</span></span> <span data-ttu-id="10c7c-105"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, sınıfının yerini alır <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-105">The <xref:System.Xml.Xsl.XslCompiledTransform> class replaces the <xref:System.Xml.Xsl.XslTransform> class.</span></span> <span data-ttu-id="10c7c-106">Stil sayfaları yöntemi kullanılarak derlenir <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-106">Style sheets are compiled using the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span> <span data-ttu-id="10c7c-107">Dönüşümler yöntemi kullanılarak yürütülür <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-107">Transforms are executed using the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="10c7c-108">Aşağıdaki yordamlarda ortak XSLT görevleri gösterilmektedir ve sınıfı ile sınıf karşılaştırması kullanılarak kod karşılaştırılır <xref:System.Xml.Xsl.XslTransform> <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-108">The following procedures show common XSLT tasks, and compare the code using the <xref:System.Xml.Xsl.XslTransform> class versus the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
### <a name="to-transform-a-file-and-output-to-a-uri"></a><span data-ttu-id="10c7c-109">Bir dosyayı ve çıktıyı bir URI 'ye dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="10c7c-109">To transform a file and output to a URI</span></span>  
  
- <span data-ttu-id="10c7c-110">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-110">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#9](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#9)]
     [!code-vb[XML_Migration#9](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#9)]  
  
- <span data-ttu-id="10c7c-111">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-111">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#10](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#10)]
     [!code-vb[XML_Migration#10](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#10)]  
  
### <a name="to-compile-a-style-sheet-and-use-a-resolver-with-default-credentials"></a><span data-ttu-id="10c7c-112">Bir stil sayfası derlemek ve varsayılan kimlik bilgileriyle çözümleyici kullanmak için</span><span class="sxs-lookup"><span data-stu-id="10c7c-112">To compile a style sheet and use a resolver with default credentials</span></span>  
  
- <span data-ttu-id="10c7c-113">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-113">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#11)]
     [!code-vb[XML_Migration#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#11)]  
  
- <span data-ttu-id="10c7c-114">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-114">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#12](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#12)]
     [!code-vb[XML_Migration#12](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#12)]  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="10c7c-115">XSLT parametresi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="10c7c-115">To use an XSLT parameter</span></span>  
  
- <span data-ttu-id="10c7c-116">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-116">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#13](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#13)]
     [!code-vb[XML_Migration#13](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#13)]  
  
- <span data-ttu-id="10c7c-117">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-117">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#14](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#14)]
     [!code-vb[XML_Migration#14](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#14)]  
  
### <a name="to-enable-xslt-scripting"></a><span data-ttu-id="10c7c-118">XSLT komut dosyalarını etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="10c7c-118">To enable XSLT scripting</span></span>  
  
- <span data-ttu-id="10c7c-119">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-119">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#15](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#15)]
     [!code-vb[XML_Migration#15](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#15)]  
  
- <span data-ttu-id="10c7c-120">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-120">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
     [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
### <a name="to-load-the-results-into-a-dom-object"></a><span data-ttu-id="10c7c-121">Sonuçları DOM nesnesine yüklemek için</span><span class="sxs-lookup"><span data-stu-id="10c7c-121">To load the results into a DOM object</span></span>  
  
- <span data-ttu-id="10c7c-122">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-122">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#19)]
     [!code-vb[XML_Migration#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#19)]  
  
- <span data-ttu-id="10c7c-123">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-123">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="10c7c-124"><xref:System.Xml.Xsl.XslCompiledTransform>Sınıfın, XSLT dönüştürme sonuçlarını nesne olarak döndüren bir yöntemi yoktur <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-124">The <xref:System.Xml.Xsl.XslCompiledTransform> class does not have a method that returns the XSLT transformation results as an <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="10c7c-125">Ancak, bir XML dosyasına çıktı verebilir ve XML dosyasını başka bir nesneye yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10c7c-125">However, you can output to an XML file and load the XML file into another object.</span></span>  
  
     [!code-csharp[XML_Migration#20](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#20)]
     [!code-vb[XML_Migration#20](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#20)]  
  
### <a name="to-stream-the-results-into-another-data-store"></a><span data-ttu-id="10c7c-126">Sonuçları başka bir veri deposuna akışa almak için</span><span class="sxs-lookup"><span data-stu-id="10c7c-126">To stream the results into another data store</span></span>  
  
- <span data-ttu-id="10c7c-127">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslTransform> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-127">Code using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#17](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#17)]
     [!code-vb[XML_Migration#17](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#17)]  
  
- <span data-ttu-id="10c7c-128">Sınıfını kullanan kod <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="10c7c-128">Code using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
     [!code-csharp[XML_Migration#18](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#18)]
     [!code-vb[XML_Migration#18](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#18)]  
  
## <a name="see-also"></a><span data-ttu-id="10c7c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10c7c-129">See also</span></span>

- [<span data-ttu-id="10c7c-130">XslTransform Sınıfından Geçirme</span><span class="sxs-lookup"><span data-stu-id="10c7c-130">Migrating From the XslTransform Class</span></span>](migrating-from-the-xsltransform-class.md)
- [<span data-ttu-id="10c7c-131">XslCompiledTransform Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="10c7c-131">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)
