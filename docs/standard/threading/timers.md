---
title: Süreölçerler
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 478484651bf839f842148f0b4164c9387db3b98a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584963"
---
# <a name="timers"></a>Süreölçerler
Zamanlayıcılar belirli bir zamanda çağrılan bir temsilciyi belirtmenize olanak sağlayan hafif nesnelerdir. İş parçacığı havuzundaki iş parçacığı bekleme işlemi gerçekleştirir.  
  
 Kullanarak <xref:System.Threading.Timer?displayProperty=nameWithType> sınıftır kolay. Oluşturduğunuz bir **Zamanlayıcı**, geçen bir <xref:System.Threading.TimerCallback> geri çağırma yöntemi, geri arama, bir ilk artırma ile geri çağırmaları arasındaki dönemi temsil eden bir zaman için geçirilen durumunu temsil eden bir nesne için temsilci. Bekleyen süreölçerini iptal çağrısı **Timer.Dispose** işlevi.  
  
> [!NOTE]
>  Diğer iki süreölçer sınıfı vardır. <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> Sınıfı görsel tasarımcılar ile çalışır ve kullanıcı arabirimi bağlamlarda kullanılacak demek bir denetim; kullanıcı arabirimi iş parçacığı olaylarına başlatır. <xref:System.Timers.Timer?displayProperty=nameWithType> Sınıfı türer <xref:System.ComponentModel.Component>, böylece kullanılabilir görsel tasarımcılar; ayrıca olayları başlatır, ancak üzerinde bunları başlatır bir <xref:System.Threading.ThreadPool> iş parçacığı. <xref:System.Threading.Timer?displayProperty=nameWithType> Sınıfı üzerinde geri aramalar yapacağı bir <xref:System.Threading.ThreadPool> iş parçacığı ve olay modeli hiç kullanmaz. Ayrıca, bir durum nesnesi diğer zamanlayıcılar sağlamadığı geri arama yöntemi sağlar. Son derece basit.  
  
 Aşağıdaki kod örneğinde tuşuna kadar her saniye bir saniye (1000 milisaniye cinsinden) ve çizgilerine sonra başlayan bir süreölçer başlatır **Enter** anahtarı. Zamanlayıcı başvuru içeren değişken hala çalışırken Zamanlayıcı tabi çöp toplama olmadığından emin olmak için bir sınıf düzeyi alan değildir. Agresif çöp toplama hakkında daha fazla bilgi için bkz: <xref:System.GC.KeepAlive%2A>.  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Timer>  
 [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
