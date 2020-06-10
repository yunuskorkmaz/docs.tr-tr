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
ms.openlocfilehash: df057d64feb89d1e43b938b36cb48f2f103b17d0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595394"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a>Nasıl yapılır: WSFederationHttpBinding Gücenli Oturumlarını Devre Dışı Bırakma

Bazı hizmetler federe kimlik bilgileri gerektirebilir, ancak güvenli oturumları desteklemez. Bu durumda, güvenli oturum özelliğini devre dışı bırakmanız gerekir. ' Den farklı olarak, <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.WSFederationHttpBinding> sınıfı bir hizmetle iletişim kurarken güvenli oturumları devre dışı bırakmak için bir yol sağlamaz. Bunun yerine, güvenli oturum ayarlarını bir önyükleme ile değiştiren özel bir bağlama oluşturmanız gerekir.

Bu konu başlığı altında, bir <xref:System.ServiceModel.WSFederationHttpBinding> özel bağlama oluşturmak için içindeki bağlama öğelerinin nasıl değiştirileceği gösterilmektedir. Sonuç, <xref:System.ServiceModel.WSFederationHttpBinding> Güvenli Oturumlar kullanmamasının dışında, ile aynıdır.

## <a name="to-create-a-custom-federated-binding-without-secure-session"></a>Güvenli oturum olmadan özel bir Federasyon bağlaması oluşturmak için

1. <xref:System.ServiceModel.WSFederationHttpBinding>Kod içinde imperatively veya yapılandırma dosyasından bir tane yükleyerek sınıfın bir örneğini oluşturun.

2. ' <xref:System.ServiceModel.WSFederationHttpBinding> A kopyalayın <xref:System.ServiceModel.Channels.CustomBinding> .

3. İçinde öğesini bulun <xref:System.ServiceModel.Channels.SecurityBindingElement> <xref:System.ServiceModel.Channels.CustomBinding> .

4. İçinde öğesini bulun <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> <xref:System.ServiceModel.Channels.SecurityBindingElement> .

5. Orijinali, <xref:System.ServiceModel.Channels.SecurityBindingElement> önyükleme güvenliği bağlama öğesiyle değiştirin <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> .

## <a name="example"></a>Örnek

Aşağıdaki örnek, güvenli oturum olmadan özel bir Federasyon bağlaması oluşturur.

[!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
[!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]

## <a name="compiling-the-code"></a>Kod Derleniyor

- Kod örneğini derlemek için, System. ServiceModel. dll derlemesine başvuran bir proje oluşturun.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlamalar ve Güvenlik](bindings-and-security.md)
