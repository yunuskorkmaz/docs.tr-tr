---
title: "Normal İfadelerde İş Parçacığı Güvenliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4cfa24da8083eac01275ad76f5c2db974b39a25
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="thread-safety-in-regular-expressions"></a>Normal İfadelerde İş Parçacığı Güvenliği
<xref:System.Text.RegularExpressions.Regex> Sınıfının kendisini iş parçacığı güvenli ve değişmez (salt okunur) değil. Diğer bir deyişle, **Regex** nesneler hiçbir iş parçacığı üzerinde oluşturulan ve iş parçacıkları arasında paylaşılan; eşleşen yöntem herhangi bir iş parçacığından çağrılabilir ve hiçbir zaman herhangi bir genel durum alter.  
  
 Ancak, sonuç nesnelerini (**eşleşme** ve **MatchCollection**) tarafından döndürülen **Regex** tek bir iş parçacığında kullanılmalıdır. Bu nesnelerin çoğunu mantıksal olarak değişmez olsa da, kendi uygulamalarını performansını artırmak için bazı sonuçlarının hesaplama geciktirebilir ve sonuç olarak, arayanlar onlara erişimi seri gerekir.  
  
 Paylaşmak için bir gereksinimi varsa **Regex** sonuç nesneleri birden çok iş parçacığı üzerinde bu nesnelerin dönüştürülebilir iş parçacığı örneklerine eşitlenmiş yöntemleriyle çağırarak. Numaralandırmalar, hariç olmak üzere tüm normal ifade sınıfları iş parçacığı açısından güvenlidir veya iş parçacığı nesneleri eşitlenmiş bir yöntemle dönüştürülebilir.  
  
 Numaralandırmalar tek özel durumdur. Bir uygulama çağrıları koleksiyonunun numaralandırmalar için seri hale gerekir. Bir koleksiyon birden çok iş parçacığı üzerinde aynı anda numaralandırılabilecek, numaralandırıcı yöntemleri tarafından Numaralandırıcı geçiş koleksiyonunun kök nesnede eşitlenmesi gerektiğini kuralıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET normal ifadeler](../../../docs/standard/base-types/regular-expressions.md)
