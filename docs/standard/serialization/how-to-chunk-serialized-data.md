---
title: "Nasıl yapılır: seri hale getirilmiş veriler öbek"
ms.date: 03/30/2017
ms.prod: .net
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- chunking serialized data
- data chunking
- binary serialization, chunking data
- large data set chunking
- serialization, chunking data
- serialization, examples
- binary serialization, examples
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 769dcbd554f8b39fbe449a8e3a6b379a7472a38f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-chunk-serialized-data"></a><span data-ttu-id="4ae39-102">Nasıl yapılır: seri hale getirilmiş veriler öbek</span><span class="sxs-lookup"><span data-stu-id="4ae39-102">How to: chunk serialized data</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="4ae39-103">Büyük veri kümeleri, Web hizmeti iletilerinde gönderirken oluşan iki sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4ae39-103">Two issues that occur when sending large data sets in Web service messages are:</span></span>  
  
1.  <span data-ttu-id="4ae39-104">Serileştirme motoruna tarafından arabelleğe alma nedeni büyük çalışma kümesi (bellek).</span><span class="sxs-lookup"><span data-stu-id="4ae39-104">A large working set (memory) due to buffering by the serialization engine.</span></span>  
  
2.  <span data-ttu-id="4ae39-105">İnordinate bant genişliği kullanımını Base64 kodlama sonra 33 yüzde Enflasyon nedeniyle.</span><span class="sxs-lookup"><span data-stu-id="4ae39-105">Inordinate bandwidth consumption due to 33 percent inflation after Base64 encoding.</span></span>  
  
 <span data-ttu-id="4ae39-106">Bu sorunları çözmek için uygulama <xref:System.Xml.Serialization.IXmlSerializable> seri hale getirme ve seri durumdan çıkarma denetlemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="4ae39-106">To solve these problems, implement the <xref:System.Xml.Serialization.IXmlSerializable> interface to control the serialization and deserialization.</span></span> <span data-ttu-id="4ae39-107">Özellikle, uygulayan <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> ve <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> verileri öbek için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="4ae39-107">Specifically, implement the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> methods to chunk the data.</span></span>  
  
### <a name="to-implement-server-side-chunking"></a><span data-ttu-id="4ae39-108">Sunucu tarafı parçalama uygulamak için</span><span class="sxs-lookup"><span data-stu-id="4ae39-108">To implement server-side chunking</span></span>  
  
1.  <span data-ttu-id="4ae39-109">Sunucu makinede, Web yöntemi gerekir ASP.NET arabelleğe almayı devre dışı kapatmak ve gerçekleştiren bir tür dönmek <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="4ae39-109">On the server machine, the Web method must turn off ASP.NET buffering and return a type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
2.  <span data-ttu-id="4ae39-110">Uygulayan türü <xref:System.Xml.Serialization.IXmlSerializable> verileri chunks <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4ae39-110">The type that implements <xref:System.Xml.Serialization.IXmlSerializable> chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
### <a name="to-implement-client-side-processing"></a><span data-ttu-id="4ae39-111">İstemci tarafında işleme uygulamak için</span><span class="sxs-lookup"><span data-stu-id="4ae39-111">To implement client-side processing</span></span>  
  
1.  <span data-ttu-id="4ae39-112">Web yöntemi uygulayan türü döndürmek için istemci proxy'de alter <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="4ae39-112">Alter the Web method on the client proxy to return the type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="4ae39-113">Kullanabileceğiniz bir <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> için otomatik olarak bunu, ancak bu burada gösterilen değil.</span><span class="sxs-lookup"><span data-stu-id="4ae39-113">You can use a <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> to do this automatically, but this isn't shown here.</span></span>  
  
2.  <span data-ttu-id="4ae39-114">Uygulama <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> öbekli veri akışı ve bayt diske yazma okumak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="4ae39-114">Implement the <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> method to read the chunked data stream and write the bytes to disk.</span></span> <span data-ttu-id="4ae39-115">Bu uygulama aynı zamanda bir ilerleme çubuğu gibi bir grafik denetimi tarafından kullanılan ilerleme olayları başlatır.</span><span class="sxs-lookup"><span data-stu-id="4ae39-115">This implementation also raises progress events that can be used by a graphic control, such as a progress bar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ae39-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ae39-116">Example</span></span>  
<span data-ttu-id="4ae39-117">Aşağıdaki kod örneği, ASP.NET arabelleğe almayı devre dışı etkinleştiren istemcideki Web yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ae39-117">The following code example shows the Web method on the client that turns off ASP.NET buffering.</span></span> <span data-ttu-id="4ae39-118">Ayrıca istemci-tarafı uygulaması gösterir <xref:System.Xml.Serialization.IXmlSerializable> verileri chunks arabirimi <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4ae39-118">It also shows the client-side implementation of the <xref:System.Xml.Serialization.IXmlSerializable> interface that chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
[!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4ae39-119">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="4ae39-119">Compiling the code</span></span>  
  
-   <span data-ttu-id="4ae39-120">Aşağıdaki ad kodunu kullanır: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, ve <xref:System.Xml.Schema>.</span><span class="sxs-lookup"><span data-stu-id="4ae39-120">The code uses the following namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, and <xref:System.Xml.Schema>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ae39-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ae39-121">See also</span></span>  
 [<span data-ttu-id="4ae39-122">Özel seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="4ae39-122">Custom Serialization</span></span>](custom-serialization.md)
