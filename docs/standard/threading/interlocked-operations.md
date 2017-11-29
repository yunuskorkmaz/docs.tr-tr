---
title: "Birbirine Kenetlenmiş İşlemler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 122058b7e826e27fe6c60c5b07610f7c63e64f78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="interlocked-operations"></a>Birbirine Kenetlenmiş İşlemler
<xref:System.Threading.Interlocked> Sınıfı birden çok iş parçacığı tarafından paylaşılan bir değişken erişimi eşitlemek yöntemler sağlar. Değişken paylaşılan bellekte ise iş parçacıkları farklı işlemler, bu mekanizma kullanabilirsiniz. Birbirine kenetlenmiş işlemler atomik — diğer bir deyişle, tüm işlem aynı değişkeni ınterlocked başka bir işlem tarafından kesilemez bir birimdir. Bu, bir iş parçacığı bir bellek adresi, ancak önce alter ve depolamak için Fırsat sahip bir değer yüklendikten sonra askıya alınabilir işletim sistemlerinde PreEmptive tarafından ile çoklu iş parçacığı kullanımı, önemlidir.  
  
 <xref:System.Threading.Interlocked> Sınıfı, aşağıdaki işlemleri sağlar:  
  
-   .NET Framework sürüm 2.0, <xref:System.Threading.Interlocked.Add%2A> yöntemi bir tamsayı değeri bir değişkene ekler ve yeni değişkenin değeri olarak döndürür.  
  
-   .NET Framework sürüm 2.0, <xref:System.Threading.Interlocked.Read%2A> yöntemi bir 64-bit tamsayı değeri atomik bir işlem olarak okur. Bu bir 64-bit tamsayı okuma normalde atomik bir işlem olduğu 32-bit işletim sistemlerinde yararlıdır.  
  
-   <xref:System.Threading.Interlocked.Increment%2A> Ve <xref:System.Threading.Interlocked.Decrement%2A> yöntemleri artırın veya bir değişken azaltma ve çıkan değeri döndürür.  
  
-   <xref:System.Threading.Interlocked.Exchange%2A> Yöntemi, o değer ve yeni değerle yerine belirtilen bir değişkende değerinin atomik bir exchange gerçekleştirir. Bu yöntemin bir genel aşırı .NET Framework sürüm 2. 0'da, bu exchange herhangi başvuru türünde bir değişken gerçekleştirmek için kullanılır. Bkz: <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.  
  
-   <xref:System.Threading.Interlocked.CompareExchange%2A> Yöntemi de alış verişleri iki değerleri, ancak bir karşılaştırma sonucu üzerinde contingent. Bu yöntemin bir genel aşırı .NET Framework sürüm 2. 0'da, bu exchange herhangi başvuru türünde bir değişken gerçekleştirmek için kullanılır. Bkz: <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.  
  
 Modern işlemcilerde yöntemlerinin <xref:System.Threading.Interlocked> sınıfı tarafından tek bir yönerge genellikle uygulanabilir. Bu nedenle, bunlar çok yüksek performanslı eşitleme sağlamak ve üst düzey eşitleme mekanizmaları oluşturmak için kullanılan ister döndürme kilitler.  
  
 Kullanan bir örnek <xref:System.Threading.Monitor> ve <xref:System.Threading.Interlocked> bileşimi sınıflara bakın [izleyicileri](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
## <a name="compareexchange-example"></a>CompareExchange örneği  
 <xref:System.Threading.Interlocked.CompareExchange%2A> Yöntemi, basit artırma ve azaltma daha karmaşık hesaplamalar korumak için kullanılabilir. Aşağıdaki örnek, bir kayan olarak depolanan toplam ekleyen bir iş parçacığı yöntemi gösterir nokta sayısı. (Tamsayılar, <xref:System.Threading.Interlocked.Add%2A> daha basit bir çözüm yöntemidir.) Tam kod örnekleri için bkz: aşırı <xref:System.Threading.Interlocked.CompareExchange%2A> tek duyarlıklı ve çift duyarlıklı kayan nokta değişkenleri alın (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> ve <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a>Exchange ve CompareExchange türsüz aşırı yüklemeleri  
 <xref:System.Threading.Interlocked.Exchange%2A> Ve <xref:System.Threading.Interlocked.CompareExchange%2A> yöntemlerine sahip türünde bağımsız değişkenler almayan aşırı <xref:System.Object>. İlk bağımsız değişken her birinin bu aşırı `ref Object` (`ByRef … As Object` Visual Basic'te), ve tür güvenliği gerektiren bu bağımsız değişken olarak kesinlikle yazılması için geçirilen değişken <xref:System.Object>; yazmak için ilk bağımsız değişken yalnızca atanamaz <xref:System.Object> Bu yöntemleri çağrılırken.  
  
> [!NOTE]
>  .NET Framework sürüm 2. 0'da, genel aşırı kullanmak <xref:System.Threading.Interlocked.Exchange%2A> ve <xref:System.Threading.Interlocked.CompareExchange%2A> kesinlikle gönderip almak için yöntemleri yazılan değişkenler.  
  
 Aşağıdaki kod örneğinde türünde bir özellik gösterir `ClassA` ayarlanabilecek yalnızca bir kez, .NET Framework sürüm 1.0 veya 1.1 uygulanan.  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.Monitor>  
 [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
 [İş parçacığı nesneleri ve özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
