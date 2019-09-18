---
title: 'Nasıl yapılır: Uygulama Etki Alanını Boşaltma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7419725f3822622a8e4210d4f3f5d8e9e59dbdd
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053126"
---
# <a name="how-to-unload-an-application-domain"></a>Nasıl yapılır: Uygulama Etki Alanını Boşaltma
Bir uygulama etki alanını kullanmayı bitirdiğinizde <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metodunu kullanarak kaldırın. **Unload** yöntemi, belirtilen uygulama etki alanını düzgün bir şekilde kapatır. Kaldırma işlemi sırasında, uygulama etki alanına hiçbir yeni iş parçacığı erişemez ve tüm uygulama etki alanına özgü veri yapıları serbest bırakılır.  
  
 Uygulama etki alanına yüklenen derlemeler kaldırılır ve artık kullanılamaz. Uygulama etki alanındaki bir derleme etki alanı Tarafsız ise, derleme verileri tüm işlem kapanana kadar bellekte kalır. İşlemin tamamını kapatmaktan başka bir etki alanı nötr derlemeyi kaldırma mekanizması yoktur. Bir uygulama etki alanını kaldırma isteğinin çalışmamasına ve bir <xref:System.CannotUnloadAppDomainException>ile sonuçlanmasına neden olan durumlar vardır.  
  
 Aşağıdaki örnek adlı `MyDomain`yeni bir uygulama etki alanı oluşturur, konsola bazı bilgileri yazdırır ve ardından uygulama etki alanını kaldırır. Kodu daha sonra, kaldırılan uygulama etki alanının kolay adını konsola yazdırmaya çalışır. Bu eylem, programın sonundaki try/catch deyimleri tarafından işlenen bir özel durum oluşturur.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama etki alanlarıyla programlama](application-domains.md#programming-with-application-domains)
- [Nasıl yapılır: Uygulama etki alanı oluşturma](how-to-create-an-application-domain.md)
- [Uygulama Etki Alanlarını Kullanma](use.md)
