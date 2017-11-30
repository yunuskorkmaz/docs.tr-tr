---
title: "Nasıl yapılır: Uygulama Etki Alanını Boşaltma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 58fd1477715bafa4e3455a3e476acbae3a098dbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-unload-an-application-domain"></a>Nasıl yapılır: Uygulama Etki Alanını Boşaltma
Uygulama etki alanı ile işiniz bittiğinde, kullanarak unload <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> yöntemi. **Unload** yöntemi, belirtilen uygulama etki alanı düzgün biçimde kapatır. Kaldırma işlemi sırasında hiçbir yeni iş parçacıkları uygulama etki alanı erişebilir ve tüm uygulama etki alanı – özel veri yapıları serbest.  
  
 Uygulama etki alanına yüklenmiş derlemeleri kaldırılır ve artık kullanılamaz. Bütünleştirilmiş uygulama etki alanındaki etki alanı neutral ise, veri derleme için bütün işlem kapatılana kadar bellekte kalır. Tüm işlem kapatılıyor dışında bir etki alanı Tarafsız derleme kaldırmak için bir mekanizma yoktur. Burada bir uygulama etki alanını boşaltma isteği çalışmaz ve sonuçlanır durumlar vardır bir <xref:System.CannotUnloadAppDomainException>.  
  
 Aşağıdaki örnek olarak adlandırılan yeni bir uygulama etki alanı oluşturur `MyDomain`, bazı bilgileri konsola yazdırır ve uygulama etki alanı kaldırır. Kodu daha sonra konsola bellekten uygulama etki alanı kolay adını yazdırmak çalışır olduğunu unutmayın. Bu eylem, program sonunda try/catch deyimleri tarafından işlenen bir özel durum oluşturur.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulama etki alanları ile programlama](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [Nasıl yapılır: uygulama etki alanı oluşturma](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 [Uygulama etki alanlarını kullanma](../../../docs/framework/app-domains/use.md)
