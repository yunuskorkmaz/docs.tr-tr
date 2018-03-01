---
title: "Dizileri Bağımsız Değişkenler Olarak Geçirme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f152173b747a171052ab99f261ed91ced9465fdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Dizileri Bağımsız Değişkenler Olarak Geçirme (C# Programlama Kılavuzu)
Dizileri bağımsız değişkenler olarak yöntemi parametrelerine geçirilebilir. Diziler başvuru türleri olduğundan, yöntemi öğelerinin değerini değiştirebilirsiniz.  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a>Tek boyutlu diziler bağımsız değişkenler olarak geçirme  
 Başlatılmış bir tek boyutlu dizi yönteme geçirebilirsiniz. Örneğin, aşağıdaki deyim yazdırma yöntemi için bir dizi gönderir.  
  
 [!code-csharp[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 Aşağıdaki kod bir kısmi yazdırma yöntemi gösterir.  
  
 [!code-csharp[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 Başlatma ve tek bir adımda aşağıdaki örnekte gösterildiği gibi yeni bir dizi geçirin.  
  
 [!code-csharp[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte, bir dizeler dizisi başlatılır ve bağımsız değişken olarak geçirilen bir `PrintArray` dizeleri yöntemi. Yöntem dizinin öğelerini görüntüler. Ardından, yöntemleri `ChangeArray` ve `ChangeArrayElement` bir dizi bağımsız değişkeni değere göre gönderme değişiklikleri dizi öğelerine engellemez olduğunu göstermek için çağrılır.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a>Çok boyutlu diziler bağımsız değişkenler olarak geçirme  
 Tek boyutlu dizi geçirdiğiniz aynı şekilde başlatılmış boyutlu bir diziye bir yönteme geçirin.  
  
 [!code-csharp[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 Aşağıdaki kod, iki boyutlu bir dizi bağımsız değişkeni olarak kabul eden bir yazdırma yöntemini kısmi bildirimini gösterir.  
  
 [!code-csharp[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 Başlatma ve tek bir adımda aşağıdaki örnekte gösterildiği gibi yeni bir dizi geçirin.  
  
 [!code-csharp[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte, iki boyutlu dizisi başlatılır ve geçirilen `Print2DArray` yöntemi. Yöntem dizinin öğelerini görüntüler.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Diziler](../../../csharp/programming-guide/arrays/index.md)  
 [Tek boyutlu diziler](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Çok boyutlu diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Basit diziler](../../../csharp/programming-guide/arrays/jagged-arrays.md)
