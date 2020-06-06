---
title: 'Nasıl yapılır: öbek serileştirilmiş veriler'
description: Büyük veri kümeleriyle sorunları önlemek için verileri öbek oluşturabilirsiniz. Serileştirme ve seri durumdan çıkarma denetlemek için IXmlSerializable arabirimini uygulayın.
ms.date: 03/30/2017
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
ms.openlocfilehash: 860fdcae0d1937f53ee964d9d4631ec812b3d379
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "83379135"
---
# <a name="how-to-chunk-serialized-data"></a><span data-ttu-id="7d096-104">Nasıl yapılır: öbek serileştirilmiş veriler</span><span class="sxs-lookup"><span data-stu-id="7d096-104">How to: chunk serialized data</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="7d096-105">Büyük veri kümeleri, Web hizmeti iletilerinde gönderirken oluşan iki sorunlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7d096-105">Two issues that occur when sending large data sets in Web service messages are:</span></span>  
  
1. <span data-ttu-id="7d096-106">Serileştirme motoruna tarafından arabelleğe alma nedeni büyük çalışma kümesi (bellek).</span><span class="sxs-lookup"><span data-stu-id="7d096-106">A large working set (memory) due to buffering by the serialization engine.</span></span>  
  
2. <span data-ttu-id="7d096-107">İnordinate bant genişliği kullanımını Base64 kodlama sonra 33 yüzde Enflasyon nedeniyle.</span><span class="sxs-lookup"><span data-stu-id="7d096-107">Inordinate bandwidth consumption due to 33 percent inflation after Base64 encoding.</span></span>  
  
 <span data-ttu-id="7d096-108">Bu sorunları gidermek için, <xref:System.Xml.Serialization.IXmlSerializable> serileştirme ve seri durumdan çıkarmayı denetlemek üzere arabirimini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="7d096-108">To solve these problems, implement the <xref:System.Xml.Serialization.IXmlSerializable> interface to control the serialization and deserialization.</span></span> <span data-ttu-id="7d096-109">Özellikle, uygulayan <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> ve <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> verileri öbek için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="7d096-109">Specifically, implement the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> methods to chunk the data.</span></span>  
  
### <a name="to-implement-server-side-chunking"></a><span data-ttu-id="7d096-110">Sunucu tarafı parçalama uygulamak için</span><span class="sxs-lookup"><span data-stu-id="7d096-110">To implement server-side chunking</span></span>  
  
1. <span data-ttu-id="7d096-111">Sunucu makinede, Web yöntemi gerekir ASP.NET arabelleğe almayı devre dışı kapatmak ve gerçekleştiren bir tür dönmek <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="7d096-111">On the server machine, the Web method must turn off ASP.NET buffering and return a type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
2. <span data-ttu-id="7d096-112">Uygulayan türü <xref:System.Xml.Serialization.IXmlSerializable> verileri chunks <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7d096-112">The type that implements <xref:System.Xml.Serialization.IXmlSerializable> chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
### <a name="to-implement-client-side-processing"></a><span data-ttu-id="7d096-113">İstemci tarafında işleme uygulamak için</span><span class="sxs-lookup"><span data-stu-id="7d096-113">To implement client-side processing</span></span>  
  
1. <span data-ttu-id="7d096-114">Web yöntemi uygulayan türü döndürmek için istemci proxy'de alter <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="7d096-114">Alter the Web method on the client proxy to return the type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="7d096-115">Bunu <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> otomatik olarak yapmak için kullanabilirsiniz, ancak burada gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="7d096-115">You can use a <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> to do this automatically, but this isn't shown here.</span></span>  
  
2. <span data-ttu-id="7d096-116"><xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A>Öbekli veri akışını okumak ve baytları diske yazmak için yöntemini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="7d096-116">Implement the <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> method to read the chunked data stream and write the bytes to disk.</span></span> <span data-ttu-id="7d096-117">Bu uygulama, ilerleme çubuğu gibi bir grafik denetimi tarafından kullanılabilecek ilerleme olayları da oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d096-117">This implementation also raises progress events that can be used by a graphic control, such as a progress bar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d096-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d096-118">Example</span></span>  
<span data-ttu-id="7d096-119">Aşağıdaki kod örneği, ASP.NET arabelleğe almayı devre dışı etkinleştiren istemcideki Web yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d096-119">The following code example shows the Web method on the client that turns off ASP.NET buffering.</span></span> <span data-ttu-id="7d096-120">Ayrıca istemci-tarafı uygulaması gösterir <xref:System.Xml.Serialization.IXmlSerializable> verileri chunks arabirimi <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7d096-120">It also shows the client-side implementation of the <xref:System.Xml.Serialization.IXmlSerializable> interface that chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
[!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7d096-121">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="7d096-121">Compiling the code</span></span>  
  
- <span data-ttu-id="7d096-122">Aşağıdaki ad kodunu kullanır: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, ve <xref:System.Xml.Schema>.</span><span class="sxs-lookup"><span data-stu-id="7d096-122">The code uses the following namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, and <xref:System.Xml.Schema>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d096-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d096-123">See also</span></span>

- [<span data-ttu-id="7d096-124">Özel serileştirme</span><span class="sxs-lookup"><span data-stu-id="7d096-124">Custom Serialization</span></span>](custom-serialization.md)
