---
title: 'Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 6559392527bb02afe9cea61e704f1f371c6d5470
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781659"
---
# <a name="how-to-turn-off-deferred-loading"></a>Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma
Giderek ertelenmiş yüklemeyi <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> `false`devre dışı bırakabilirsiniz. Daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](deferred-versus-immediate-loading.md).  
  
> [!NOTE]
> Ertelenmiş yükleme, nesne izleme kapalıyken etkili bir şekilde kapalıdır. Daha fazla bilgi için [nasıl yapılır: Bilgileri salt okuma](how-to-retrieve-information-as-read-only.md)olarak alın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ' i ' ye <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> `false`ayarlayarak ertelenmiş yüklemenin nasıl kapatılacağı gösterilmektedir.  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
- [Veritabanını Sorgulama](querying-the-database.md)
