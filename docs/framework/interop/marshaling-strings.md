---
title: Dizeleri Hazırlama
description: Dizelerin nasıl hazırlanacağını gözden geçirin. Sonuç olarak, bir yapıda veya bir sınıfta değere ya da başvuruya göre dizeleri sıralama ve daha fazla bilgi için seçeneklere bakın.
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
ms.openlocfilehash: 11925e3e126620788bb09e90e4d2528dbaf56581
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547772"
---
# <a name="marshaling-strings"></a>Dizeleri Hazırlama
Platform çağrısı, dize parametrelerini kopyalar, bu parametreleri .NET Framework biçiminden (Unicode) yönetilmeyen biçimde (ANSI), gerekirse. Yönetilen dizeler sabit olduğu için, platform çağırma işlevi, işlev döndürdüğü zaman yönetilen belleğe geri kopyalamaz.  
  
 Aşağıdaki tabloda dizeler için sıralama seçenekleri listelenmekte, kullanımları açıklanmakta ve karşılık gelen .NET Framework örneğine bir bağlantı sağlanmıştır.  
  
|Dize|Description|Örnek|  
|------------|-----------------|------------|  
|Değere göre.|Dizeleri parametrelerde olduğu gibi geçirir.|[MsgBox](msgbox-sample.md)|  
|Sonuç olarak.|Yönetilmeyen koddan dizeleri döndürür.|[Dizeler](/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|Başvuruya göre.|Dizeleri kullanılarak gelen/giden parametreler olarak geçirir <xref:System.Text.StringBuilder> .|[Arabellek](/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100))|  
|Değere göre bir yapıda.|Dizeleri bir ın parametresi olan bir yapıda geçirir.|[Yapılar](/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100))|  
|Başvuruya göre bir yapıda **(Char \* )**.|Dizeleri bir ın/out parametresi olan bir yapıda geçirir. Yönetilmeyen işlev bir karakter arabelleği işaretçisi bekler ve arabellek boyutu yapının bir üyesidir.|[Dizeler](/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|Başvuruya göre bir yapıda **(Char [])**.|Dizeleri bir ın/out parametresi olan bir yapıda geçirir. Yönetilmeyen işlev, gömülü bir karakter arabelleği bekliyor.|[OSINFO](/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|Değere göre bir sınıfta **(Char \* )**.|Bir sınıftaki dizeleri geçirir (bir sınıf bir ın/out parametresidir). Yönetilmeyen işlev bir karakter arabelleği işaretçisi bekliyor.|[OpenFileDlg](/previous-versions/dotnet/netframework-4.0/w5tyztk9(v=vs.100))|  
|Değere göre bir sınıfta **(Char [])**.|Bir sınıftaki dizeleri geçirir (bir sınıf bir ın/out parametresidir). Yönetilmeyen işlev, gömülü bir karakter arabelleği bekliyor.|[OSINFO](/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|Değere göre dizeler dizisi olarak.|Değer ile geçirilen dizelerin dizisini oluşturur.|[Diziler](marshaling-different-types-of-arrays.md)|  
|Değere göre dizeler içeren yapıların bir dizisi olarak.|Dizeler içeren bir yapı dizisi oluşturur ve dizi değere göre geçirilir.|[Diziler](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dizeler için Varsayılan Hazırlama](default-marshaling-for-strings.md)
- [Platform Çağırma ile Veri Sıralama](marshaling-data-with-platform-invoke.md)
- [Sınıflar, Yapılar ve Birleşimleri Hazırlama](marshaling-classes-structures-and-unions.md)
- [Farklı Dizi Türlerini Hazırlama](marshaling-different-types-of-arrays.md)
- [Çeşitli sıralama örnekleri](/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))
