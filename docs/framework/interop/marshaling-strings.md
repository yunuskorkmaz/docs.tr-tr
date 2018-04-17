---
title: Dizeleri Hazırlama
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
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
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: adcdf55f3e33a48c4fd10ea243bb0ce3497f522f
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
---
# <a name="marshaling-strings"></a>Dizeleri Hazırlama
Platform çağırma bunları .NET Framework biçimden (Unicode) yönetilmeyen biçimi (ANSI), gerekirse dönüştürme kopyaları dizesi parametreleri. Yönetilen dizeleri değişmez olduğundan, platform çağırma işlevi döndüğünde bunları yönetilmeyen bellekten yönetilen bellek kopyalamaz.  
  
 Aşağıdaki tabloda dizeleri sıralama seçeneklerini listeler, bunların kullanım açıklar ve karşılık gelen .NET Framework örnek bağlantı sağlar.  
  
|Dize|Açıklama|Örnek|  
|------------|-----------------|------------|  
|Değer tarafından.|Dizeleri parametreleri olduğu gibi geçirir.|[MsgBox](msgbox-sample.md)|  
|Sonuç olarak.|Yönetilmeyen kod dizelerden döndürür.|[Dizeler](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))|  
|Başvuruya göre.|Dizeleri olarak giriş/çıkış kullanarak parametrelerini geçirir <xref:System.Text.StringBuilder>.|[Arabellekler](https://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100))|  
|Değere göre bir yapısında.|Dizeleri bir giriş parametresi bir yapısında geçirir.|[Yapılar](https://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e(v=vs.100))|  
|Başvuruya göre bir yapı **(char\*)**.|Dizeleri giriş/çıkış parametresi bir yapısında geçirir. Yönetilmeyen işlev karakter arabellek için bir işaretçi bekler ve arabellek boyutu yapısı bir üyesidir.|[Dizeler](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))|  
|Başvuruya göre bir yapı **(char[])**.|Dizeleri giriş/çıkış parametresi bir yapısında geçirir. Yönetilmeyen işlevi bir katıştırılmış karakter arabellek bekliyor.|[Osınfo](https://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455(v=vs.100))|  
|Değere göre bir sınıftaki **(char\*)**.|Dizeler (bir sınıf bir giriş/çıkış parametresine olan) bir sınıfta geçirir. Yönetilmeyen işlev karakter arabellek için bir işaretçi bekliyor.|[OpenFileDlg](https://msdn.microsoft.com/library/b7dea792-cb92-4baf-ac7b-6a24803e6c75(v=vs.100))|  
|Değere göre bir sınıftaki **(char[])**.|Dizeler (bir sınıf bir giriş/çıkış parametresine olan) bir sınıfta geçirir. Yönetilmeyen işlevi bir katıştırılmış karakter arabellek bekliyor.|[Osınfo](https://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455(v=vs.100))|  
|Değere göre bir dizeler dizisi.|Değeri tarafından geçirilen bir dizeler dizisi oluşturur.|[Diziler](marshaling-different-types-of-arrays.md)|  
|Değere göre dizelerini içeren yapıları dizisi.|Yapıları dizisi oluşturan dizeler içeriyor ve dizi değere göre geçirilir.|[Diziler](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Platform Çağırma ile Veri Hazırlama](marshaling-data-with-platform-invoke.md)  
 [Platform çağırma veri türleri](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [Sınıflar, Yapılar ve Birleşimleri Hazırlama](marshaling-classes-structures-and-unions.md)  
 [Türlerin dizileri sıralama](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))  
 [Çeşitli hazırlama örnekleri](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))
