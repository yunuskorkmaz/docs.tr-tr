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
ms.openlocfilehash: 0db33d59d1fc1c19e07567108970db77059cebb7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223036"
---
# <a name="marshaling-strings"></a>Dizeleri Hazırlama
Platform çağırma bunları (Unicode) .NET Framework biçiminden yönetilmeyen biçimine (ANSI) gerekirse dönüştürme kopyaları dizesi parametreleri. Yönetilen dizeler sabit olduğundan, platform çağırma işlevi döndüğünde bunları yönetilmeyen bellekten yönetilen bellek kopyalamaz.  
  
 Aşağıdaki tabloda, dizeler için sıralama seçeneklerini listeler, bunların kullanımını açıklar ve karşılık gelen .NET Framework örnek bir bağlantı sağlar.  
  
|Dize|Açıklama|Örnek|  
|------------|-----------------|------------|  
|Değere göre.|Parametreleri olduğu gibi dizeleri geçirir.|[MsgBox](msgbox-sample.md)|  
|Sonuç olarak.|Dizeleri, yönetilmeyen koddan döndürür.|[Dizeler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|Başvuruya göre.|Dizeler olarak In/Out parametreleri kullanarak geçirir <xref:System.Text.StringBuilder>.|[Arabellekler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100))|  
|Değere göre bir yapıda.|Dizeleri bir giriş parametresi bir yapıda geçirir.|[Yapılar](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100))|  
|Başvuruya göre bir yapı **(char\*)**.|Dizeleri bir ın/Out parametresi bir yapıda geçirir. Yönetilmeyen işlev işaretçisi karakter arabelleği bekliyor ve arabellek boyutu yapısı bir üyesidir.|[Dizeler](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|Başvuruya göre bir yapı **(char[])**.|Dizeleri bir ın/Out parametresi bir yapıda geçirir. Yönetilmeyen işlev, bir katıştırılmış karakter arabelleği bekliyor.|[Osınfo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|Değer sınıfında **(char\*)**.|Dizeler (bir sınıf bir ın/Out parametresi olan) bir sınıfta geçirir. Yönetilmeyen işlev işaretçisi karakter arabelleği bekliyor.|[OpenFileDlg](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w5tyztk9(v=vs.100))|  
|Değer sınıfında **(char[])**.|Dizeler (bir sınıf bir ın/Out parametresi olan) bir sınıfta geçirir. Yönetilmeyen işlev, bir katıştırılmış karakter arabelleği bekliyor.|[Osınfo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|Değer bir dize dizisi.|Değere göre geçirilen bir dize dizisi oluşturur.|[Diziler](marshaling-different-types-of-arrays.md)|  
|Değere göre dizeleri içeren yapılarını dizisi.|Yapıları dizisi oluşturan dizeleri içeren ve bir dizi değere göre geçirilir.|[Diziler](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Platform Çağırma ile Veri Sıralama](marshaling-data-with-platform-invoke.md)
- [Sınıflar, Yapılar ve Birleşimleri Hazırlama](marshaling-classes-structures-and-unions.md)
- [Farklı Dizi Türlerini Hazırlama](marshaling-different-types-of-arrays.md)
- [Çeşitli Sıralama Örnekleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))
