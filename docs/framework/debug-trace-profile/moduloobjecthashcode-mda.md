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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1679e283a801044ad5a0baed89f17e6acc74259c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052453"
---
# <a name="moduloobjecthashcode-mda"></a>moduloObjectHashcode MDA
Yönetilen hata ayıklama Yardımcısı (MDA), <xref:System.Object> sınıfının davranışını, <xref:System.Object.GetHashCode%2A> yöntemi tarafından döndürülen karma kodda bir mod işlemi gerçekleştirmek için değiştirir. `moduloObjectHashcode` Bu mda için varsayılan mod 1 ' dir ve tüm nesneler <xref:System.Object.GetHashCode%2A> için 0 döndürmesine neden olur.  
  
## <a name="symptoms"></a>Belirtiler  
 Ortak dil çalışma zamanının (CLR) yeni bir sürümüne taşıdıktan sonra, bir program artık düzgün şekilde çalışmaz:  
  
- Program, öğesinden yanlış bir <xref:System.Collections.Hashtable>nesne alıyor.  
  
- Bir <xref:System.Collections.Hashtable> öğesinden numaralandırmanın sırası, programı kesen bir değişikliğe sahiptir.  
  
- Eşit olmak için kullanılan iki nesne artık eşit değildir.  
  
- Eşit olmaması için kullanılan iki nesne artık eşittir.  
  
## <a name="cause"></a>Sebep  
 <xref:System.Collections.Hashtable> Yöntemi, anahtarın içindeki <xref:System.Object.Equals%2A> yöntemi, çağrı sonuçlarını <xref:System.Object.GetHashCode%2A> yönteme göre karşılaştırarak, anahtar <xref:System.Collections.Hashtable> için sınıfındaki bir nesne için uygulama bir öğesinden yanlış nesneyi alıyor olabilir . Kendi alanları farklı değerlere sahip olsa bile iki nesne aynı karma koda sahip olabileceğinden, nesne eşitliğini test etmek için karma kodları kullanılmamalıdır. Bu karma kod çakışmaları, ancak uygulamada nadir olarak ortaya çıkar. Bunun bir <xref:System.Collections.Hashtable> aramada sahip olduğu efekt, eşit olmayan iki anahtarın eşit gibi görüneceği ve <xref:System.Collections.Hashtable>öğesinden yanlış nesne döndürüldüğü anlamına gelir. Performans nedenleriyle, ' nin <xref:System.Object.GetHashCode%2A> uygulanması çalışma zamanı sürümleri arasında değişebilir, bu nedenle, bir sürümde gerçekleşmeyecek olan çakışmalar sonraki sürümlerde meydana gelebilir. Bu MDA ' i etkinleştirerek, karma kodları çarpışdığınızda kodunuzun hatalara sahip olup olmadığını test edin. Etkinleştirildiğinde bu mda, <xref:System.Object.GetHashCode%2A> yöntemin 0 döndürmesini sağlar, sonuçta tüm karma kodlarının çakışmasına neden olur. Bu MDA ' i etkinleştiren tek efekt, programınızın daha yavaş çalışmasına neden olur.  
  
 Anahtar değişikliği için karma kodları hesaplamak <xref:System.Collections.Hashtable> üzere kullanılan algoritma bir çalışma zamanının bir sürümünden diğerine değişebilir. Programınızın bir karma tablonun anahtar veya değer listesi sırasına göre bağımlılığı yapıp gerçekleştirmediğini test etmek için bu MDA ' yi etkinleştirebilirsiniz.  
  
## <a name="resolution"></a>Çözüm  
 Karma kodları, nesne kimliği için bir alternatif olarak hiçbir şekilde kullanmayın. Karma kodlarını karşılaştırmayan <xref:System.Object.Equals%2A?displayProperty=nameWithType> yöntemi geçersiz kılmayı uygulayın.  
  
 Karma tablolardaki anahtarların veya değerlerin numaralandırmalar sırasıyla bağımlılıklar oluşturmayın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA etkinleştirildiğinde uygulamalar daha yavaş çalışır. Bu MDA yalnızca döndürülen karma kodu alır ve bunun yerine, bir mod ile ayrıldığınızda kalanı döndürür.  
  
## <a name="output"></a>Çıkış  
 Bu MDA için çıkış yok.  
  
## <a name="configuration"></a>Yapılandırma  
 `modulus` Öznitelik, karma kodunda kullanılan mod 'u belirtir. Varsayılan değer 1’dir.  
  
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
