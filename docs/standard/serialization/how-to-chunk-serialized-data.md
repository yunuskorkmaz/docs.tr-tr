---
title: 'Nasıl yapılır: öbek serileştirilmiş veriler'
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
ms.openlocfilehash: 6a39997d8854d525146c044ed4bbf939de615d3f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602431"
---
# <a name="how-to-chunk-serialized-data"></a>Nasıl yapılır: öbek serileştirilmiş veriler

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Büyük veri kümeleri, Web hizmeti iletilerinde gönderirken oluşan iki sorunlar şunlardır:  
  
1. Serileştirme motoruna tarafından arabelleğe alma nedeni büyük çalışma kümesi (bellek).  
  
2. İnordinate bant genişliği kullanımını Base64 kodlama sonra 33 yüzde Enflasyon nedeniyle.  
  
 Bu sorunları gidermek için, serileştirme ve <xref:System.Xml.Serialization.IXmlSerializable> seri durumdan çıkarmayı denetlemek üzere arabirimini uygulayın. Özellikle, uygulayan <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> ve <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> verileri öbek için yöntemleri.  
  
### <a name="to-implement-server-side-chunking"></a>Sunucu tarafı parçalama uygulamak için  
  
1. Sunucu makinede, Web yöntemi gerekir ASP.NET arabelleğe almayı devre dışı kapatmak ve gerçekleştiren bir tür dönmek <xref:System.Xml.Serialization.IXmlSerializable>.  
  
2. Uygulayan türü <xref:System.Xml.Serialization.IXmlSerializable> verileri chunks <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> yöntemi.  
  
### <a name="to-implement-client-side-processing"></a>İstemci tarafında işleme uygulamak için  
  
1. Web yöntemi uygulayan türü döndürmek için istemci proxy'de alter <xref:System.Xml.Serialization.IXmlSerializable>. Bunu otomatik olarak yapmak <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> için kullanabilirsiniz, ancak burada gösterilmez.  
  
2. Öbekli <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> veri akışını okumak ve baytları diske yazmak için yöntemini uygulayın. Bu uygulama, ilerleme çubuğu gibi bir grafik denetimi tarafından kullanılabilecek ilerleme olayları da oluşturur.  
  
## <a name="example"></a>Örnek  
Aşağıdaki kod örneği, ASP.NET arabelleğe almayı devre dışı etkinleştiren istemcideki Web yöntemini gösterir. Ayrıca istemci-tarafı uygulaması gösterir <xref:System.Xml.Serialization.IXmlSerializable> verileri chunks arabirimi <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> yöntemi.  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
[!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a>Kod derleme  
  
- Aşağıdaki ad kodunu kullanır: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, ve <xref:System.Xml.Schema>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel serileştirme](custom-serialization.md)
