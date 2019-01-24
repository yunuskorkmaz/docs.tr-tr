---
title: Beyanlar ve Kaynaklara Erişimi Reddetme
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: df35ea2f01f96b044763c696434e5ede39d6b4bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715757"
---
# <a name="claims-and-denying-access-to-resources"></a>Beyanlar ve Kaynaklara Erişimi Reddetme
Windows Communication Foundation (WCF) bir beyana dayalı yetkilendirme mekanizması destekler. Talep varlığını temel alarak kaynaklara erişimine yanı sıra sistemleri genellikle talep varlığını temel alarak kaynaklara erişimi reddetme. Bu sistemlere incelemelisiniz <xref:System.IdentityModel.Policy.AuthorizationContext> aramadan önce erişimine izin verilmesinden neden talepler için erişimin reddedilmesi neden talepler için.  
  
 Örneğin, bir sistem bir kaynağa erişim izni olan herkes bir talep türü ile reddetmek, `Age`, sağ <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, kaynak değerini `Under 21` yalnızca o kimlik da bir talep türü olduğunda `Name`, sağ <xref:System.IdentityModel.Claims.Rights.Identity%2A>, Kaynak değeri `Mallory`. Başka bir deyişle, sistem erişimi herkes tarafından altında 21 yaşında olduğunu ve adı Mallory olduğunda erişim verir engeller. Bu doğru uygulamak için anlamsal, aranacak önemlidir `Age` ilk talep ve yaş altında 21 yaşında olup olmadığını belirler. Mallory 21'altında varsa, aksi takdirde, daha sonra kaynak yalnızca temeline göre erişim verilebilir `Name` talep.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Kimlik Modeliyle Talep ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Talepler ve Belirteçler](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
