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
ms.openlocfilehash: 4d5f98229c3a9da69a350ae325cd42e8deb6b7bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119842"
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
- [Nasıl yapılır: Uygulama Etki Alanı Oluşturma](how-to-create-an-application-domain.md)
- [Uygulama Etki Alanlarını Kullanma](use.md)
