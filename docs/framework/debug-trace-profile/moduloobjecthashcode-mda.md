---
title: moduloObjectHashcode MDA
description: ModuloObjectHashcode yönetilen hata ayıklama Yardımcısı 'nı (MDA) gözden geçirin. Bu, nesne sınıfını bir GetHashCode Yöntem sonucu üzerinde geri kalan bir değer elde etmek için değiştirir.
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
ms.openlocfilehash: a929ec2b9196f1f6cad0528fdf7323839a86fa55
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052071"
---
# <a name="moduloobjecthashcode-mda"></a>moduloObjectHashcode MDA
`moduloObjectHashcode`Yönetilen hata ayıklama Yardımcısı (MDA), sınıfının davranışını, <xref:System.Object> yöntemi tarafından döndürülen karma kodda bir mod işlemi gerçekleştirmek için değiştirir <xref:System.Object.GetHashCode%2A> . Bu MDA için varsayılan mod 1 ' dir ve <xref:System.Object.GetHashCode%2A> tüm nesneler için 0 döndürmesine neden olur.  
  
## <a name="symptoms"></a>Belirtiler  
 Ortak dil çalışma zamanının (CLR) yeni bir sürümüne taşıdıktan sonra, bir program artık düzgün şekilde çalışmaz:  
  
- Program, öğesinden yanlış bir nesne alıyor <xref:System.Collections.Hashtable> .  
  
- Bir öğesinden numaralandırmanın sırası, <xref:System.Collections.Hashtable> programı kesen bir değişikliğe sahiptir.  
  
- Eşit olmak için kullanılan iki nesne artık eşit değildir.  
  
- Eşit olmaması için kullanılan iki nesne artık eşittir.  
  
## <a name="cause"></a>Nedeni  
 Yöntemi, <xref:System.Collections.Hashtable> <xref:System.Object.Equals%2A> <xref:System.Collections.Hashtable> çağrı sonuçlarını yönteme göre karşılaştırarak, anahtarın sınıf üzerindeki yöntemi, anahtar için olan yöntem için yanlış nesneyi alıyor olabilir <xref:System.Object.GetHashCode%2A> . Kendi alanları farklı değerlere sahip olsa bile iki nesne aynı karma koda sahip olabileceğinden, nesne eşitliğini test etmek için karma kodları kullanılmamalıdır. Bu karma kod çakışmaları, ancak uygulamada nadir olarak ortaya çıkar. Bunun bir aramada sahip olduğu efekt, <xref:System.Collections.Hashtable> eşit olmayan iki anahtarın eşit gibi görüneceği ve öğesinden yanlış nesne döndürüldüğü anlamına gelir <xref:System.Collections.Hashtable> . Performans nedenleriyle, ' nin uygulanması <xref:System.Object.GetHashCode%2A> çalışma zamanı sürümleri arasında değişebilir, bu nedenle, bir sürümde gerçekleşmeyecek olan çakışmalar sonraki sürümlerde meydana gelebilir. Bu MDA ' i etkinleştirerek, karma kodları çarpışdığınızda kodunuzun hatalara sahip olup olmadığını test edin. Etkinleştirildiğinde bu MDA, <xref:System.Object.GetHashCode%2A> yöntemin 0 döndürmesini sağlar, sonuçta tüm karma kodlarının çakışmasına neden olur. Bu MDA ' i etkinleştiren tek efekt, programınızın daha yavaş çalışmasına neden olur.  
  
 <xref:System.Collections.Hashtable>Anahtar değişikliği için karma kodları hesaplamak üzere kullanılan algoritma bir çalışma zamanının bir sürümünden diğerine değişebilir. Programınızın bir karma tablonun anahtar veya değer listesi sırasına göre bağımlılığı yapıp gerçekleştirmediğini test etmek için bu MDA ' yi etkinleştirebilirsiniz.  
  
## <a name="resolution"></a>Çözüm  
 Karma kodları, nesne kimliği için bir alternatif olarak hiçbir şekilde kullanmayın. <xref:System.Object.Equals%2A?displayProperty=nameWithType>Karma kodlarını karşılaştırmayan yöntemi geçersiz kılmayı uygulayın.  
  
 Karma tablolardaki anahtarların veya değerlerin numaralandırmalar sırasıyla bağımlılıklar oluşturmayın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA etkinleştirildiğinde uygulamalar daha yavaş çalışır. Bu MDA yalnızca döndürülen karma kodu alır ve bunun yerine, bir mod ile ayrıldığınızda kalanı döndürür.  
  
## <a name="output"></a>Çıktı  
 Bu MDA için çıkış yok.  
  
## <a name="configuration"></a>Yapılandırma  
 `modulus`Öznitelik, karma kodunda kullanılan mod 'u belirtir. Varsayılan değer 1’dir.  
  
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
