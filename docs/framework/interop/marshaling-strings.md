---
title: Dizeleri Hazırlama
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc4f40ab954a3bb31e0b55aad8c00ed2ee63f6c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514900"
---
# <a name="marshaling-strings"></a>Dizeleri Hazırlama
Platform çağırma bunları (Unicode) .NET Framework biçiminden yönetilmeyen biçimine (ANSI) gerekirse dönüştürme kopyaları dizesi parametreleri. Yönetilen dizeler sabit olduğundan, platform çağırma işlevi döndüğünde bunları yönetilmeyen bellekten yönetilen bellek kopyalamaz.  
  
 Aşağıdaki tabloda, dizeler için sıralama seçeneklerini listeler, bunların kullanımını açıklar ve karşılık gelen .NET Framework örnek bir bağlantı sağlar.  
  
|Dize|Açıklama|Örnek|  
|------------|-----------------|------------|  
|Değere göre.|Parametreleri olduğu gibi dizeleri geçirir.|[MsgBox](msgbox-sample.md)|  
|Sonuç olarak.|Dizeleri, yönetilmeyen koddan döndürür.|[Dizeler](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))|  
|Başvuruya göre.|Dizeler olarak In/Out parametreleri kullanarak geçirir <xref:System.Text.StringBuilder>.|[Arabellekler](https://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100))|  
|Değere göre bir yapıda.|Dizeleri bir giriş parametresi bir yapıda geçirir.|[Yapılar](https://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e(v=vs.100))|  
|Başvuruya göre bir yapı **(char\*)**.|Dizeleri bir ın/Out parametresi bir yapıda geçirir. Yönetilmeyen işlev işaretçisi karakter arabelleği bekliyor ve arabellek boyutu yapısı bir üyesidir.|[Dizeler](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))|  
|Başvuruya göre bir yapı **(char[])**.|Dizeleri bir ın/Out parametresi bir yapıda geçirir. Yönetilmeyen işlev, bir katıştırılmış karakter arabelleği bekliyor.|[Osınfo](https://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455(v=vs.100))|  
|Değer sınıfında **(char\*)**.|Dizeler (bir sınıf bir ın/Out parametresi olan) bir sınıfta geçirir. Yönetilmeyen işlev işaretçisi karakter arabelleği bekliyor.|[OpenFileDlg](https://msdn.microsoft.com/library/b7dea792-cb92-4baf-ac7b-6a24803e6c75(v=vs.100))|  
|Değer sınıfında **(char[])**.|Dizeler (bir sınıf bir ın/Out parametresi olan) bir sınıfta geçirir. Yönetilmeyen işlev, bir katıştırılmış karakter arabelleği bekliyor.|[Osınfo](https://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455(v=vs.100))|  
|Değer bir dize dizisi.|Değere göre geçirilen bir dize dizisi oluşturur.|[Diziler](marshaling-different-types-of-arrays.md)|  
|Değere göre dizeleri içeren yapılarını dizisi.|Yapıları dizisi oluşturan dizeleri içeren ve bir dizi değere göre geçirilir.|[Diziler](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Platform Çağırma ile Veri Hazırlama](marshaling-data-with-platform-invoke.md)
- [Platform çağırma veri türleri](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))
- [Sınıflar, Yapılar ve Birleşimleri Hazırlama](marshaling-classes-structures-and-unions.md)
- [Tür dizilerini sıralama](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))
- [Çeşitli sıralama örnekleri](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))
