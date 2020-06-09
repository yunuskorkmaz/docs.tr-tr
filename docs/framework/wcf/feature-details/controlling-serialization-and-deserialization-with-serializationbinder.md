---
title: SerializationBinder ile Seri Hale Getirme ve Seri Halden Çıkarmayı Denetleme
ms.date: 03/30/2017
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
ms.openlocfilehash: 1101a3caf2a033b4dbbc5f45737f187c58adbef2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595576"
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>SerializationBinder ile Seri Hale Getirme ve Seri Halden Çıkarmayı Denetleme
Serileştirme sırasında, bir biçimlendirici doğru türdeki ve sürümdeki bir nesnenin örneğini oluşturmak için gereken bilgileri iletir. Bu bilgiler genellikle nesnenin tam tür adını ve derleme adını içerir. Varsayılan olarak, seri durumdan çıkarma, aynı nesnenin bir örneğini oluşturmak için bu bilgileri kullanır. Bazı kullanıcıların serileştirme ve seri durumdan çıkarılacak sınıfı, orijinal sınıfın seri durumundan çıkarma işlemi gerçekleştiren makinede olmaması, özgün sınıfın derlemeler arasında taşındığı veya sunucu ve istemcide farklı bir sınıf sürümü olması gerekebilir. Daha fazla bilgi için bkz. [serileştirme cildin kullanımı](../samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
> Bu işlevsellik yalnızca veya kullanılarak kullanılabilir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <xref:System.Runtime.Serialization.NetDataContractSerializer> .  
  
## <a name="using-serializationbinder"></a>Serializationciltçi kullanma  
 <xref:System.Runtime.Serialization.SerializationBinder>serileştirme ve seri durumundan çıkarma sırasında kullanılan gerçek türleri denetlemek için kullanılan soyut bir sınıftır. Serileştirme ve seri durumundan çıkarma sırasında kullanılan türleri denetlemek için, <xref:System.Runtime.Serialization.SerializationBinder> ve yöntemlerini geçersiz kılacak bir sınıf türet ve geçersiz kılın <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> . <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)>Yöntemi bir alır <xref:System.Type> ve bir derleme ve tür adı döndürür. <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)>Yöntemi bir derleme ve tür adı alır ve döndürür <xref:System.Type> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Serileştirme ve Seri Durumdan Çıkarma](serialization-and-deserialization.md)
- [Seri Hale Getirme Bağlayıcısı Kullanımı](../samples/usage-of-serialization-binder.md)
