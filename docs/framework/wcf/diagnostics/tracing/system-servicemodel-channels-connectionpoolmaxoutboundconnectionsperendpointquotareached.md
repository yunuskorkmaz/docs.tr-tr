---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 742e80a3115e8f8caa728e0d8c460ee8b964ddc9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84588723"
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
