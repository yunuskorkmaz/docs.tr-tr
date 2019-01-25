---
title: SerializationBinder ile Seri Hale Getirme ve Seri Durumdan Çıkarmayı Denetleme
ms.date: 03/30/2017
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
ms.openlocfilehash: 518a9bc88dd291f608f736a47a107549e399eb94
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629507"
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>SerializationBinder ile Seri Hale Getirme ve Seri Durumdan Çıkarmayı Denetleme
Serileştirme sırasında bir biçimlendirici sürümü ve doğru türde bir nesne örneğini oluşturmak için gereken bilgileri iletir. Bu bilgiler genellikle bütünleştirilmiş kod nesnesinin adını ve tam tür adını içerir. Varsayılan olarak seri durumundan çıkarma bir eşdeğer nesne örneğini oluşturmak için bu bilgileri kullanır. Bazı kullanıcılar, seri hale getrime ve özgün sınıfı seri durumdan çıkarma işlemi gerçekleştirme makinesinde mevcut olmayabilir çünkü, ya da hangi sınıfının denetim gerekebilir, özgün sınıf derlemeler arasında taşınmış veya farklı bir sürüm sınıfının gereklidir Sunucu ve istemci. Daha fazla bilgi için [serileştirme Bağlayıcısı kullanımı](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
>  Bu işlev yalnızca kullanırken kullanılabilir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> veya <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
## <a name="using-serializationbinder"></a>SerializationBinder kullanma  
 <xref:System.Runtime.Serialization.SerializationBinder> bir Özet sınıf serileştirme ve seri durumundan çıkarma sırasında kullanılan gerçek türlerini denetlemek için kullanılır. Serileştirme ve seri durumundan çıkarma sırasında kullanılan türlerini denetlemek için öğesinden bir sınıf türetin <xref:System.Runtime.Serialization.SerializationBinder> ve geçersiz kılma <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> ve <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> yöntemleri. <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> Yöntemi bir <xref:System.Type> ve bir derleme ve tür adını döndürür. <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> Yöntemi bir bütünleştirilmiş kod ve tür adını alır ve döndürür bir <xref:System.Type>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Serileştirme ve Seri Durumdan Çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)
- [Serileştirme Bağlayıcısı Kullanımı](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
