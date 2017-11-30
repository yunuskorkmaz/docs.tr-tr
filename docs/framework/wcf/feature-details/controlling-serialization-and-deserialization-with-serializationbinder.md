---
title: "SerializationBinder ile Seri Hale Getirme ve Seri Durumdan Çıkarmayı Denetleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c3180d62824f94e27e02c80e09fdf32252f0a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>SerializationBinder ile Seri Hale Getirme ve Seri Durumdan Çıkarmayı Denetleme
Serileştirme sırasında bir biçimlendirici doğru türü ve sürümü bir nesne örneğini oluşturmak için gereken bilgileri iletir. Bu bilgiler genelde derleme nesnesinin adını ve tam tür adını içerir. Varsayılan olarak, seri durumdan çıkarma aynı nesne örneğini oluşturmak için bu bilgileri kullanır. Bazı kullanıcılar, hangi sınıfının seri hale getirmek ve seri durumdan çıkarma gerçekleştirme makinede özgün sınıfı olmayabilir için ya da seri durumdan kontrol gerekebilir, özgün sınıf derlemeler arasında taşınmış veya sınıf farklı bir sürümü gerekiyor. Sunucu ve istemci. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Seri hale getirme Bağlayıcısı kullanımı](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
>  Bu işlevsellik yalnızca kullanırken kullanılabilir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> veya <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
## <a name="using-serializationbinder"></a>SerializationBinder kullanma  
 <xref:System.Runtime.Serialization.SerializationBinder>bir Özet sınıf, seri hale getirme ve seri durumdan çıkarma sırasında kullanılan gerçek türlerini denetlemek için kullanılır. Serileştirme ve seri durumundan çıkarma sırasında kullanılan türlerini denetlemek için öğesinden bir sınıf türetin <xref:System.Runtime.Serialization.SerializationBinder> ve geçersiz kılma <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False & autoUpgrade = True ve <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)? qualifyHint = False & autoUpgrade = True yöntemleri. <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False & autoUpgrade = True metodu bir <xref:System.Type> ve bir derleme ve tür adını döndürür. <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False & autoUpgrade = True yöntemi alır derleme ve tür adı ve döndürür bir <xref:System.Type>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Seri hale getirme ve seri durumdan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [Seri hale getirme Bağlayıcısı kullanımı](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
