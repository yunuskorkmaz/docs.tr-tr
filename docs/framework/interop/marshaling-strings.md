---
title: "Dizeleri Hazırlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, samples
- platform invoke, marshaling data
- data marshaling, strings
- data marshaling, samples
- data marshaling, platform invoke
- marshaling. strings
- marshaling, platform invoke
- sample applications [.NET Framework], marshaling strings
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89dace5ba946f2c6bd1384f23ffcff797e99bdd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-strings"></a>Dizeleri Hazırlama
Platform çağırma bunları .NET Framework biçimden (Unicode) yönetilmeyen biçimi (ANSI), gerekirse dönüştürme kopyaları dizesi parametreleri. Yönetilen dizeleri değişmez olduğundan, platform çağırma işlevi döndüğünde bunları yönetilmeyen bellekten yönetilen bellek kopyalamaz.  
  
 Aşağıdaki tabloda dizeleri sıralama seçeneklerini listeler, bunların kullanım açıklar ve karşılık gelen .NET Framework örnek bağlantı sağlar.  
  
|Dize|Açıklama|Örnek|  
|------------|-----------------|------------|  
|Değer tarafından.|Dizeleri parametreleri olduğu gibi geçirir.|[MsgBox](../../../docs/framework/interop/msgbox-sample.md)|  
|Sonuç olarak.|Yönetilmeyen kod dizelerden döndürür.|[Dizeler](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|Başvuruya göre.|Dizeleri olarak giriş/çıkış kullanarak parametrelerini geçirir <xref:System.Text.StringBuilder>.|[Arabellekler](http://msdn.microsoft.com/en-us/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|Değere göre bir yapısında.|Dizeleri bir giriş parametresi bir yapısında geçirir.|[Yapılar](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|Başvuruya göre bir yapı **(char\*)**.|Dizeleri giriş/çıkış parametresi bir yapısında geçirir. Yönetilmeyen işlev karakter arabellek için bir işaretçi bekler ve arabellek boyutu yapısı bir üyesidir.|[Dizeler](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|Başvuruya göre bir yapı **(char[])**.|Dizeleri giriş/çıkış parametresi bir yapısında geçirir. Yönetilmeyen işlevi bir katıştırılmış karakter arabellek bekliyor.|[Osınfo](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|Değere göre bir sınıftaki **(char\*)**.|Dizeler (bir sınıf bir giriş/çıkış parametresine olan) bir sınıfta geçirir. Yönetilmeyen işlev karakter arabellek için bir işaretçi bekliyor.|[OpenFileDlg](http://msdn.microsoft.com/en-us/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|Değere göre bir sınıftaki **(char[])**.|Dizeler (bir sınıf bir giriş/çıkış parametresine olan) bir sınıfta geçirir. Yönetilmeyen işlevi bir katıştırılmış karakter arabellek bekliyor.|[Osınfo](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|Değere göre bir dizeler dizisi.|Değeri tarafından geçirilen bir dizeler dizisi oluşturur.|[Diziler](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|Değere göre dizelerini içeren yapıları dizisi.|Yapıları dizisi oluşturan dizeler içeriyor ve dizi değere göre geçirilir.|[Diziler](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Platform Çağırma ile Veri Hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 [Platform çağırma veri türleri](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [Sınıflar, Yapılar ve Birleşimleri Hazırlama](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md)  
 [Türlerin dizileri sıralama](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)  
 [Çeşitli hazırlama örnekleri](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)
