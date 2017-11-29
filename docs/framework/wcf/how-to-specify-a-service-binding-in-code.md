---
title: "Nasıl yapılır: Kodda Hizmet Bağlama Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 64d33b268c736b3dba333b767bee7fedb487397b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-a-service-binding-in-code"></a>Nasıl yapılır: Kodda Hizmet Bağlama Belirtme
Bu örnekte, bir `ICalculator` anlaşma hesaplayıcı hizmeti için tanımlanan, hizmet içinde uygulanan `CalculatorService` sınıfı ve kendi uç noktası burada belirtilen hizmet kullanmalısınız kodda tanımlanan <xref:System.ServiceModel.BasicHttpBinding> sınıfı.  
  
 Bağlama ve adres bilgilerini yapılandırma yerine imperatively kod bildirimli olarak belirtmek için genellikle en iyi uygulamadır. Bağlamalar ve dağıtılmış bir hizmet için adresleri hizmet geliştirildiği sırada kullanılan olanlardan genellikle farklı olduğu için uç noktalar kodda tanımlama genellikle pratik değildir. Daha genel olarak, bağlama tutulması ve adresleme bilgilerini kodu dışında yeniden derleyin veya uygulamayı yeniden dağıtmak zorunda kalmadan değiştirmek için bunları sağlar.  
  
 Yapılandırma öğeleri kullanılarak kod yerine bu hizmetinin nasıl yapılandırılacağı açıklaması için bkz: [nasıl yapılır: yapılandırmada hizmet bağlama belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a>BasicHttpBinding hizmeti için kullanacağınız kodu belirtmek için  
  
1.  Hizmet türü için bir hizmet sözleşmesini tanımlama.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2.  Bir hizmet sınıfında Hizmet sözleşmesini uygulama.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3.  Barındırma uygulamasında hizmet ve hizmetle birlikte kullanılacak bağlama için taban adresi oluşturma.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4.  Ana bilgisayar hizmeti oluşturmak, uç nokta ekleyin ve konak açın.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Bağlama özelliklerinin varsayılan değerlerini değiştirmek için  
  
1.  Varsayılan özellik değerlerini birini değiştirmek için <xref:System.ServiceModel.BasicHttpBinding> sınıfı, ana bilgisayar oluşturmadan önce yeni bir değer bağlama özellik değerini ayarlayın. Örneğin, 2 dakika olarak 1 dakikalık varsayılan açma ve kapama zaman aşımı değerlerini değiştirmek için aşağıdakileri kullanın.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetler ve istemcileri yapılandırmak için bağlamaları kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Bir uç noktası adresi belirtme](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
