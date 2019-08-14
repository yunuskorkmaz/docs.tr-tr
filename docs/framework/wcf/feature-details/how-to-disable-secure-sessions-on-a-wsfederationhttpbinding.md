---
title: 'Nasıl yapılır: WSFederationHttpBinding Gücenli Oturumlarını Devre Dışı Bırakma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
ms.openlocfilehash: 810c5b127a34fb0a35e8fd2d83ff59e00aca0ba1
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972044"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a>Nasıl yapılır: WSFederationHttpBinding Gücenli Oturumlarını Devre Dışı Bırakma

Bazı hizmetler federe kimlik bilgileri gerektirebilir, ancak güvenli oturumları desteklemez. Bu durumda, güvenli oturum özelliğini devre dışı bırakmanız gerekir. 'Denfarklıolarak,sınıfıbirhizmetleiletişimkurarkengüvenlioturumlarıdevredışıbırakmakiçinbiryolsağlamaz.<xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.WSFederationHttpBinding> Bunun yerine, güvenli oturum ayarlarını bir önyükleme ile değiştiren özel bir bağlama oluşturmanız gerekir.

Bu konu başlığı altında, bir <xref:System.ServiceModel.WSFederationHttpBinding> özel bağlama oluşturmak için içindeki bağlama öğelerinin nasıl değiştirileceği gösterilmektedir. Sonuç, güvenli oturumlar kullanmamasının <xref:System.ServiceModel.WSFederationHttpBinding> dışında, ile aynıdır.

## <a name="to-create-a-custom-federated-binding-without-secure-session"></a>Güvenli oturum olmadan özel bir Federasyon bağlaması oluşturmak için

1. Kod içinde imperatively veya yapılandırma <xref:System.ServiceModel.WSFederationHttpBinding> dosyasından bir tane yükleyerek sınıfın bir örneğini oluşturun.

2. <xref:System.ServiceModel.WSFederationHttpBinding> ' A<xref:System.ServiceModel.Channels.CustomBinding>kopyalayın.

3. <xref:System.ServiceModel.Channels.SecurityBindingElement> İçinde<xref:System.ServiceModel.Channels.CustomBinding>öğesini bulun.

4. <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> İçinde<xref:System.ServiceModel.Channels.SecurityBindingElement>öğesini bulun.

5. Orijinali <xref:System.ServiceModel.Channels.SecurityBindingElement> , önyükleme güvenliği bağlama öğesiyle <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>değiştirin.

## <a name="example"></a>Örnek

Aşağıdaki örnek, güvenli oturum olmadan özel bir Federasyon bağlaması oluşturur.

[!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
[!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]

## <a name="compiling-the-code"></a>Kod Derleniyor

- Kod örneğini derlemek için, System. ServiceModel. dll derlemesine başvuran bir proje oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlamalar ve Güvenlik](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
