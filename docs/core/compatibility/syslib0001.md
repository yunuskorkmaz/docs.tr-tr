---
title: SYSLIB0001 uyarısı
description: Derleme zamanı uyarı SYSLIB0001 üreten kullanım dışı meler hakkında bilgi edinin.
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 58c16879b7d91598ea0848bb0ba95f8fa0200cfe
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333353"
---
# <a name="syslib0001-the-utf-7-encoding-is-insecure"></a>SYSLIB0001: UTF-7 kodlaması güvenli değil

UTF-7 kodlaması artık uygulamalar arasında geniş bir kullanım değildir ve birçok adım artık değişim içinde [kullanımını](https://security.stackexchange.com/a/68609/3573) dengeler. Ayrıca, UTF-7 kodlu verilerle karşılaşmayı düşünmeyin uygulamalarda [saldırı vektörü olarak da kullanılır](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) . Microsoft, <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> hata algılaması sağlamadığı için kullanımını uyarır.

Sonuç olarak, aşağıdaki API 'Ler .NET 5,0 ' den itibaren kullanılmıyor olarak işaretlenir. Bu API 'lerin kullanımı, `SYSLIB0001` derleme zamanında uyarı oluşturur.

- <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> özelliði
- <xref:System.Text.UTF7Encoding.%23ctor%2A> Kurucu

## <a name="workarounds"></a>Geçici Çözümler

- <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>Ya da <xref:System.Text.UTF7Encoding> kendi protokolde veya dosya biçimindeyse kullanıyorsanız:

  Veya kullanarak geçiş <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> yapın <xref:System.Text.UTF8Encoding> . UTF-8 endüstri standardıdır ve diller, işletim sistemleri ve çalışma zamanları genelinde yaygın olarak desteklenir. UTF-8 kullanımı, kodunuzun gelecekteki bakımını kolaylaştırır ve ekosisteminin geri kalanı ile daha birlikte çalışabilir hale gelir.

- Bir örneği karşılaştırıyorsanız <xref:System.Text.Encoding> <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> :

  Bunun yerine, iyi bilinen UTF-7 kod sayfasına karşı bir denetim gerçekleştirmeyi göz önünde bulundurun `65000` . Kod sayfasıyla karşılaştırıldığında, uyarıyı önleyin ve aynı zamanda türü bir veya alt sınıfı olarak çağırırın gibi bazı uç durumları da idare edersiniz `new UTF7Encoding()` .

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

## <a name="see-also"></a>Ayrıca bkz.

- [UTF-7 kod yolları artık kullanılmıyor](3.1-5.0.md#utf-7-code-paths-are-obsolete)
