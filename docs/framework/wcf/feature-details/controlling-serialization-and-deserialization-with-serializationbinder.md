---
title: SerializationBinder ile Seri Hale Getirme ve Seri Durumdan Çıkarmayı Denetleme
ms.date: 03/30/2017
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
ms.openlocfilehash: 3252413606f4aaf45a825d8d0a6f4af8763ef6be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>SerializationBinder ile Seri Hale Getirme ve Seri Durumdan Çıkarmayı Denetleme
Serileştirme sırasında bir biçimlendirici doğru türü ve sürümü bir nesne örneğini oluşturmak için gereken bilgileri iletir. Bu bilgiler genelde derleme nesnesinin adını ve tam tür adını içerir. Varsayılan olarak, seri durumdan çıkarma aynı nesne örneğini oluşturmak için bu bilgileri kullanır. Bazı kullanıcılar, hangi sınıfının seri hale getirmek ve seri durumdan çıkarma gerçekleştirme makinede özgün sınıfı olmayabilir için ya da seri durumdan kontrol gerekebilir, özgün sınıf derlemeler arasında taşınmış veya sınıf farklı bir sürümü gerekiyor. Sunucu ve istemci. Daha fazla bilgi için bkz: [seri hale getirme Bağlayıcısı kullanımı](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
>  Bu işlevsellik yalnızca kullanırken kullanılabilir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> veya <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
## <a name="using-serializationbinder"></a>SerializationBinder kullanma  
 <xref:System.Runtime.Serialization.SerializationBinder> bir Özet sınıf, seri hale getirme ve seri durumdan çıkarma sırasında kullanılan gerçek türlerini denetlemek için kullanılır. Serileştirme ve seri durumundan çıkarma sırasında kullanılan türlerini denetlemek için öğesinden bir sınıf türetin <xref:System.Runtime.Serialization.SerializationBinder> ve geçersiz kılma <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> ve <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> yöntemleri. <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> Metodu bir <xref:System.Type> ve bir derleme ve tür adını döndürür. <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> Yöntemi bir derleme ve tür adını alır ve döndüren bir <xref:System.Type>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Serileştirme ve Seri Durumdan Çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [Serileştirme Bağlayıcısı Kullanımı](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
