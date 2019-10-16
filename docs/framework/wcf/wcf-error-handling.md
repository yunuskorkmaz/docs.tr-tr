---
title: WCF Hata İşleme
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: 7e5c65da3fa13a3640c7a6948f1284d0c6ffdfc4
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319941"
---
# <a name="wcf-error-handling"></a>WCF Hata İşleme
Bir WCF uygulaması tarafından karşılaşılan hatalar üç gruptan birine aittir:  
  
1. İletişim hataları  
  
2. Ara sunucu/kanal hataları  
  
3. Uygulama hataları  
  
 İletişim hataları, bir ağ kullanılamadığında, bir istemci yanlış bir adres kullandığında veya hizmet ana bilgisayarı gelen iletileri dinlemediğinde oluşur. Bu tür hatalar istemciye <xref:System.ServiceModel.CommunicationException> veya @no__t -1-türetilmiş sınıflar olarak döndürülür.  
  
 Ara sunucu/kanal hataları, kanal veya proxy içinde oluşan hatalardır. Bu tür hatalar şunlardır: kapatılmış bir proxy veya kanal kullanılmaya çalışılıyor, istemci ile hizmet arasında bir anlaşma uyumsuzluğu var veya istemcinin kimlik bilgileri hizmet tarafından reddedildi. Bu kategoride çok fazla sayıda farklı hata türü var, burada listelemek için çok fazla. Bu tür hatalar istemciye olduğu gibi döndürülür (özel durum nesnelerinde hiçbir dönüşüm gerçekleştirilmez).  
  
 Uygulama hataları, bir hizmet işleminin yürütülmesi sırasında oluşur. Bu tür hatalar istemciye <xref:System.ServiceModel.FaultException> veya <xref:System.ServiceModel.FaultException%601> olarak gönderilir.  
  
 WCF 'de hata işleme, aşağıdakilerden biri veya birkaçı tarafından gerçekleştirilir:  
  
- Oluşturulan özel durumu doğrudan işleme. Bu yalnızca iletişim ve proxy/kanal hataları için yapılır.  
  
- Hata sözleşmelerini kullanma  
  
- @No__t-0 arabirimini uygulama  
  
- @No__t-0 olaylarını işleme  
  
## <a name="fault-contracts"></a>Hata sözleşmeleri  
 Hata sözleşmeleri, hizmet işlemi sırasında platformdan bağımsız bir şekilde oluşabilecek hataları tanımlamanızı sağlar. Varsayılan olarak, bir hizmet işlemi içinden oluşturulan tüm özel durumlar istemciye <xref:System.ServiceModel.FaultException> nesnesi olarak döndürülür. @No__t-0 nesnesi çok az bilgi içerecektir. Bir hata sözleşmesi tanımlayarak ve hatayı <xref:System.ServiceModel.FaultException%601> olarak döndürerek istemciye gönderilen bilgileri kontrol edebilirsiniz. Daha fazla bilgi için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="ierrorhandler"></a>IErrorHandler  
 @No__t-0 arabirimi, WCF uygulamanızın hatalara nasıl yanıt vereceğini öğrenmek için daha fazla denetim sağlar.  İstemciye döndürülen hata iletisi üzerinde tam denetim sağlar ve günlüğe kaydetme gibi özel hata işleme gerçekleştirmenize olanak tanır.  @No__t-0 hakkında daha fazla bilgi edinmek ve [hata işleme ve raporlama üzerinde denetimi genişletmek](./samples/extending-control-over-error-handling-and-reporting.md) için  
  
## <a name="servicehost-events"></a>ServiceHost olayları  
 @No__t-0 sınıfı Hizmetleri barındırır ve hataları işlemek için gerekebilecek birkaç olayı tanımlar. Örneğin:  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceHost>
