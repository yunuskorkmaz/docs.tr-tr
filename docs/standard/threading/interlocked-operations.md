---
title: Birbirine Kenetlenmiş İşlemler
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Interlocked class, about Interlocked class
- threading [.NET Framework], Interlocked class
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6478ea94b6c54272a01497ac7b1cb1b197892309
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131071"
---
# <a name="interlocked-operations"></a>Birbirine Kenetlenmiş İşlemler
<xref:System.Threading.Interlocked> Sınıfı, birden çok iş parçacığı tarafından paylaşılan bir değişkene erişimi eşitleme yöntemler sağlar. Değişken paylaşılan bellekte ise, iş parçacıkları farklı işlemler, bu mekanizma kullanabilirsiniz. Birbirine kenetlenmiş işlemler atomik — diğer bir deyişle, tüm işlemi aynı değişken üzerinde başka bir birbirine kenetlenmiş işlem tarafından kesintiye birimidir. Burada bir iş parçacığı bir bellek adresi, ancak önce onu değiştirmenize ve depolamak için bir fırsat sahip bir değer yüklendikten sonra askıya alınmadan bu işletim sistemlerinde preemptive ile çoklu iş parçacığı önem taşır.  
  
 <xref:System.Threading.Interlocked> Sınıfı aşağıdaki işlemleri sağlar:  
  
-   .NET Framework sürüm 2.0 <xref:System.Threading.Interlocked.Add%2A> yöntemi bir tamsayı değeri bir değişkene ekler ve yeni bir değişkenin değerini döndürür.  
  
-   .NET Framework sürüm 2.0 <xref:System.Threading.Interlocked.Read%2A> yöntemi, bir 64-bit tamsayı değeri atomik işlem olarak okur. Bu bir 64-bit tamsayı okuma normalde atomik bir işlem olduğu 32-bit işletim sistemlerinde kullanışlıdır.  
  
-   <xref:System.Threading.Interlocked.Increment%2A> Ve <xref:System.Threading.Interlocked.Decrement%2A> yöntemleri artırın veya bir değişkeni azaltır ve sonuç değerini döndürür.  
  
-   <xref:System.Threading.Interlocked.Exchange%2A> Yöntemi, o değer ve yeni bir değerle değiştirmeyi belirtilen bir değişkende değeri atomik bir değişim gerçekleştirir. .NET Framework sürüm 2. 0'da, bu yöntem, genel bir aşırı yükleme, bu exchange herhangi bir başvuru türünde bir değişken üzerinde gerçekleştirmek için kullanılabilir. Bkz: <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>.  
  
-   <xref:System.Threading.Interlocked.CompareExchange%2A> Yöntemi de birbiriyle değiştirir iki değerler, ancak bir karşılaştırma sonucu topolojideki. .NET Framework sürüm 2. 0'da, bu yöntem, genel bir aşırı yükleme, bu exchange herhangi bir başvuru türünde bir değişken üzerinde gerçekleştirmek için kullanılabilir. Bkz: <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>.  
  
 Modern işlemcilerde yöntemlerinin <xref:System.Threading.Interlocked> sınıfı tek bir yönerge genellikle uygulanabilir. Bu nedenle, bunlar çok yüksek performanslı eşitlemeyi sağlaması ve daha üst düzey eşitleme mekanizmaları oluşturmak için kullanılan dönüş kilitleri ister.  
  
 Kullanan bir örnek için <xref:System.Threading.Monitor> ve <xref:System.Threading.Interlocked> birleşimi, sınıflara bakın [izleyiciler](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
## <a name="compareexchange-example"></a>CompareExchange örneği  
 <xref:System.Threading.Interlocked.CompareExchange%2A> Yöntemi, daha basit artırma ve azaltma daha karmaşık hesaplamaları korumak için kullanılabilir. Aşağıdaki örnek, bir değişken olarak depolanan toplam ekleyen bir iş parçacığı açısından güvenli yöntemi gösterir. nokta sayısı. (Tamsayılar için <xref:System.Threading.Interlocked.Add%2A> yöntemi daha basit bir çözümdür.) Tam kod örnekleri için bkz. aşırı yüklemeleri <xref:System.Threading.Interlocked.CompareExchange%2A> tek duyarlık hem çift duyarlıklı kayan nokta bağımsız değişkenleri alır (<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> ve <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>).  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## <a name="untyped-overloads-of-exchange-and-compareexchange"></a>Exchange ve CompareExchange yazılmamış aşırı yüklemeleri  
 <xref:System.Threading.Interlocked.Exchange%2A> Ve <xref:System.Threading.Interlocked.CompareExchange%2A> yöntemlerine sahip türü bağımsız değişkenleri, aşırı yüklemeler <xref:System.Object>. İlk bağımsız değişken her birinin bu aşırı yüklemeler `ref Object` (`ByRef … As Object` Visual Basic'te), ve tür güvenliği gerektirir, bu bağımsız değişken olarak kesin olarak belirlenmiş için geçirilen değişkeni <xref:System.Object>; yalnızca ilk bağımsız değişkenin türü atanamaz <xref:System.Object> Bu yöntemleri çağrılırken.  
  
> [!NOTE]
>  .NET Framework sürüm 2. 0'da, genel aşırı yüklemelerini kullanın <xref:System.Threading.Interlocked.Exchange%2A> ve <xref:System.Threading.Interlocked.CompareExchange%2A> kesin alışverişi yöntemleri türdeki değişkenler.  
  
 Aşağıdaki kod örneği vlastnost typu gösterir `ClassA` ayarlanabilecek yalnızca bir kez gibi .NET Framework sürüm 1.0 veya 1.1 uygulanabilir.  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Interlocked>  
- <xref:System.Threading.Monitor>  
- [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
