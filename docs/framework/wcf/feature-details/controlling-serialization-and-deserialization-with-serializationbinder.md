---
title: SerializationBinder ile Seri Hale Getirme ve Seri Halden Çıkarmayı Denetleme
ms.date: 03/30/2017
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
ms.openlocfilehash: 29d48560cf25cd5c2e34d7a512d8c7079c65879e
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988210"
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>SerializationBinder ile Seri Hale Getirme ve Seri Halden Çıkarmayı Denetleme
Serileştirme sırasında, bir biçimlendirici doğru türdeki ve sürümdeki bir nesnenin örneğini oluşturmak için gereken bilgileri iletir. Bu bilgiler genellikle nesnenin tam tür adını ve derleme adını içerir. Varsayılan olarak, seri durumdan çıkarma, aynı nesnenin bir örneğini oluşturmak için bu bilgileri kullanır. Bazı kullanıcıların serileştirme ve seri durumdan çıkarılacak sınıfı, orijinal sınıfın seri durumundan çıkarma işlemi gerçekleştiren makinede olmaması, özgün sınıfın derlemeler arasında taşındığı veya farklı bir sınıfın sürümü olması gerekir. sunucu ve istemci. Daha fazla bilgi için bkz. [serileştirme cildin kullanımı](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
> Bu işlevsellik yalnızca <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <xref:System.Runtime.Serialization.NetDataContractSerializer>veya kullanılarak kullanılabilir.  
  
## <a name="using-serializationbinder"></a>Serializationciltçi kullanma  
 <xref:System.Runtime.Serialization.SerializationBinder>serileştirme ve seri durumundan çıkarma sırasında kullanılan gerçek türleri denetlemek için kullanılan soyut bir sınıftır. Serileştirme ve seri durumundan çıkarma sırasında kullanılan türleri denetlemek için, <xref:System.Runtime.Serialization.SerializationBinder> <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> ve <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> yöntemlerini geçersiz kılacak bir sınıf türet ve geçersiz kılın. <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> Yöntemi bir<xref:System.Type> alır ve bir derleme ve tür adı döndürür. Yöntemi bir derleme ve tür adı alır ve <xref:System.Type>döndürür. <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Serileştirme ve Seri Durumdan Çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)
- [Serileştirme Bağlayıcısı Kullanımı](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
