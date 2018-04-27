---
title: Saklı yordamları kullanarak işlemleri özelleştirme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 5d47089092de80488fbae107da630352cb38c1d9
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="customizing-operations-by-using-stored-procedures"></a>Saklı yordamları kullanarak işlemleri özelleştirme
Saklı yordamlar varsayılan davranışı geçersiz kılma için ortak bir yaklaşım temsil eder. Bu konuda Göster nasıl kullanacağınızı örneklerde yöntemi sarmalayıcıları saklı yordamları ve nasıl saklı yordamlar doğrudan çağırabilir miyim oluşturulur.  
  
 Visual Studio kullanıyorsanız, kullanabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ekler, güncelleştirmeleri ve silme gerçekleştirmek için saklı yordamlar atamak için.  
  
> [!NOTE]
>  Geri veritabanı üretilmiş değerler okumak için saklı yordamlarda çıkış parametreleri kullanın. Çıkış parametreleri kullanamıyorsanız, geçersiz kılmalar tarafından oluşturulan güvenmek yerine bir kısmi yöntem uygulaması yazma [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Veritabanı oluşturulan değerler için eşlenen üyeyi ayarlayın, sonra uygun değerlere `INSERT` veya `UPDATE` işlemleri başarıyla tamamlandı. Daha fazla bilgi için bkz: [Geliştirici içinde geçersiz kılma varsayılan davranışı sorumluluklarını](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte, varsayımında `Northwind` sınıfı, türetilen bir sınıfta geçersiz kılmalar için kullanılmakta olan saklı yordamları çağırmak için iki yöntem içerir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#1)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki sınıf geçersiz kılma için bu yöntemleri kullanır.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#2)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Kullanabileceğiniz `NorthwindThroughSprocs` tam olarak kullanacağınız gibi `Northwnd`.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Geliştiricinin Varsayılan Davranışı Geçersiz Kılma Sorumlulukları](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
