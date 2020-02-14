---
title: moduloObjectHashcode MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
ms.openlocfilehash: 65bbdfec2d7050d1b474a8186a9ea6e9bb93bd9e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216175"
---
# <a name="moduloobjecthashcode-mda"></a>moduloObjectHashcode MDA
`moduloObjectHashcode` yönetilen hata ayıklama Yardımcısı (MDA), <xref:System.Object.GetHashCode%2A> yöntemi tarafından döndürülen karma kodda bir mod işlemi gerçekleştirmek için <xref:System.Object> sınıfının davranışını değiştirir. Bu MDA için varsayılan mod 1 ' dir ve bu, <xref:System.Object.GetHashCode%2A> tüm nesneler için 0 döndürmesine neden olur.  
  
## <a name="symptoms"></a>Belirtiler  
 Ortak dil çalışma zamanının (CLR) yeni bir sürümüne taşıdıktan sonra, bir program artık düzgün şekilde çalışmaz:  
  
- Program <xref:System.Collections.Hashtable>yanlış nesneyi alıyor.  
  
- <xref:System.Collections.Hashtable> numaralandırmanın sırası, programı kesen bir değişikliğe sahiptir.  
  
- Eşit olmak için kullanılan iki nesne artık eşit değildir.  
  
- Eşit olmaması için kullanılan iki nesne artık eşittir.  
  
## <a name="cause"></a>Nedeni  
 Bir <xref:System.Collections.Hashtable>, anahtar için sınıfındaki <xref:System.Object.Equals%2A> yönteminin, <xref:System.Object.GetHashCode%2A> yöntemine yapılan çağrının sonuçlarını karşılaştırarak, nesne eşitlik için <xref:System.Collections.Hashtable> testlerindeki yanlış nesneyi alıyor olabilir. Kendi alanları farklı değerlere sahip olsa bile iki nesne aynı karma koda sahip olabileceğinden, nesne eşitliğini test etmek için karma kodları kullanılmamalıdır. Bu karma kod çakışmaları, ancak uygulamada nadir olarak ortaya çıkar. Bunun <xref:System.Collections.Hashtable> arama üzerindeki etkisi, eşit olmayan iki anahtarın eşit olduğu gibi görüneceği ve <xref:System.Collections.Hashtable>yanlış nesnenin döndürüldüğü anlamına gelir. Performans nedenleriyle, <xref:System.Object.GetHashCode%2A> uygulanması çalışma zamanı sürümleri arasında değişebilir, bu nedenle, bir sürümde gerçekleşmeyecek olan çakışmalar sonraki sürümlerde meydana gelebilir. Bu MDA ' i etkinleştirerek, karma kodları çarpışdığınızda kodunuzun hatalara sahip olup olmadığını test edin. Etkinleştirildiğinde, bu MDA <xref:System.Object.GetHashCode%2A> yönteminin 0 döndürmesini sağlar, sonuçta tüm karma kodlarının çakışmasına neden olur. Bu MDA ' i etkinleştiren tek efekt, programınızın daha yavaş çalışmasına neden olur.  
  
 Bir <xref:System.Collections.Hashtable> numaralandırma sırası, anahtar değişikliği için karma kodları hesaplamak üzere kullanılan algoritma, çalışma zamanının bir sürümünden diğerine değişebilir. Programınızın bir karma tablonun anahtar veya değer listesi sırasına göre bağımlılığı yapıp gerçekleştirmediğini test etmek için bu MDA ' yi etkinleştirebilirsiniz.  
  
## <a name="resolution"></a>Çözüm  
 Karma kodları, nesne kimliği için bir alternatif olarak hiçbir şekilde kullanmayın. Karma kodları karşılaştırmadan <xref:System.Object.Equals%2A?displayProperty=nameWithType> yönteminin geçersiz kılmasını uygulayın.  
  
 Karma tablolardaki anahtarların veya değerlerin numaralandırmalar sırasıyla bağımlılıklar oluşturmayın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA etkinleştirildiğinde uygulamalar daha yavaş çalışır. Bu MDA yalnızca döndürülen karma kodu alır ve bunun yerine, bir mod ile ayrıldığınızda kalanı döndürür.  
  
## <a name="output"></a>Çıktı  
 Bu MDA için çıkış yok.  
  
## <a name="configuration"></a>Yapılandırma  
 `modulus` özniteliği, karma kodda kullanılan mod 'u belirtir. Varsayılan değer 1’dir.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
