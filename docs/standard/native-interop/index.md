---
title: Yerel birlikte çalışabilirlik-.NET
description: .NET ' te yerel bileşenlerle arabirim oluşturmayı öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 3ca213bc7228d2e4337607df2d47b334c5bea14f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106813"
---
# <a name="native-interoperability"></a>Native ile birlikte çalışma

Aşağıdaki makalelerde .NET içinde "yerel birlikte çalışabilirlik" yapmanın çeşitli yolları gösterilmektedir.

Yerel koda çağrı yapmak istemenizin birkaç nedeni vardır:

- İşletim sistemleri, yönetilen sınıf kitaplıklarında bulunmayan büyük bir API hacimiyle gelir. Bu senaryo için bir ana örnek, donanım veya işletim sistemi yönetim işlevlerine erişim sağlar.
- [Java Native Interface (JNı)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) aracılığıyla veya yerel bir bileşen oluşturabilecek başka bir yönetilen dilde sunulan Java kodu gibi C stili ABR 'leri (yerel absıs) oluşturan veya üreten diğer bileşenlerle iletişim kurma.
- Windows 'da, Microsoft Office Suite gibi yüklü yazılımların çoğu, programlarını temsil eden COM bileşenlerini kaydettirir ve geliştiricilerin bunları otomatikleştirebilmeleri veya onları kullanmasına izin verir. Bu, yerel birlikte çalışabilirlik de gerektirir.

Önceki listede, geliştiricinin yerel bileşenlerle arabirim istediğini/beğenmek istediği tüm olası durumlar ve senaryolar ele alınmaktadır. .NET sınıf kitaplığı, örneğin, konsol desteği ve işleme, dosya sistemi erişimi ve diğerleri gibi API 'Lerinin bir dengeli sayısını uygulamak için yerel birlikte çalışabilirlik desteğini kullanır. Ancak, gerekirse bir seçenek olduğuna dikkat edin.

> [!NOTE]
> Bu bölümdeki örneklerin çoğu, .NET Core için desteklenen üç platformda (Windows, Linux ve macOS) sunulacak. Ancak bazı Short ve tanım örneklerinde, Windows dosya adları ve uzantıları kullanan tek bir örnek gösterilir (yani, kitaplıklar için "dll"). Bu, bu özelliklerin Linux veya macOS üzerinde kullanılamadığı anlamına gelmez, ancak kolay bir sake için yapılmıştı.

## <a name="see-also"></a>Ayrıca bkz.

- [Platform çağırma (P/Invoke)](pinvoke.md)
- [Tür sıralaması](type-marshaling.md)
- [Yerel birlikte çalışabilirlik en iyi uygulamaları](best-practices.md)
