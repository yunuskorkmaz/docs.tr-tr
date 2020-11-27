---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 3e4e1ff7ea8d8768c8d902dc09bd3b78646c2caf
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256332"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a>Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure

WS-AT protokol hizmeti, belirtilen düzenleme bağlamını kullanarak bir işlem üzerinde listeleme yapamadı.  
  
## <a name="description"></a>Açıklama  

 MSDTC, belirli bir 2PC protokolü için bir işlemde listeleme işlemi yapamıyor.  İşlem artık mevcut olmadığından, en listeye artık izin verilmediği veya çok fazla sayıda liste bulunduğundan bu durum oluşabilir.  
  
## <a name="troubleshooting"></a>Sorun giderme  

 İşlem yapılabilir herhangi bir öğenin mevcut olup olmadığını öğrenmek için izleme iletisindeki durum dizesini inceleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](index.md)
- [Uygulamanızda Sorun Giderme için İzleme Kullanma](using-tracing-to-troubleshoot-your-application.md)
- [Yönetim ve tanılama](../index.md)
