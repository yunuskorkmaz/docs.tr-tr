---
title: Uygulanıp Durdurulan İşlem/Saniye
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: 6369fea6def5ebb6b62274caed31d5fb63b3b0e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998198"
---
# <a name="transacted-operations-aborted-per-second"></a>Uygulanıp Durdurulan İşlem/Saniye
Sayaç adı: Saniye başına durdurulan işlemler.  
  
## <a name="description"></a>Açıklama  
 Bir saniye içinde bu hizmet durdurulmuş işlem alt işlemlerinin sayısı.  
  
 Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)
