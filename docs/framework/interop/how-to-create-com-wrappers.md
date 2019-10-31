---
title: 'Nasıl yapılır: COM Sarmalayıcıları Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
ms.openlocfilehash: 623df8aa86d25d9a57d3039bee01b0ee39d402a8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123934"
---
# <a name="how-to-create-com-wrappers"></a>Nasıl yapılır: COM Sarmalayıcıları Oluşturma

Visual Studio 2005 özelliklerini veya .NET Framework araçları Tlbimp. exe ve Regasm. exe ' yi kullanarak bileşen nesne modeli (COM) sarmalayıcıları oluşturabilirsiniz. Her iki yöntem de iki tür COM sarmalayıcıları üretir:

- Yönetilen kodda bir COM nesnesi çalıştırmak için bir tür kitaplığından bir [çalışma zamanı çağrılabilir sarmalayıcı](../../standard/native-interop/runtime-callable-wrapper.md) .

- Yerel bir uygulamada yönetilen bir nesne çalıştırmak için gerekli kayıt defteri ayarlarına sahip [com çağrılabilir sarmalayıcı](../../standard/native-interop/com-callable-wrapper.md) .

Visual Studio 2005 ' de COM sarmalayıcısı ' ı projenize bir başvuru olarak ekleyebilirsiniz.

## <a name="wrap-com-objects-in-a-managed-application"></a>Yönetilen bir uygulamadaki COM nesnelerini sarın

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a>Visual Studio kullanarak bir çalışma zamanı çağrılabilir sarmalayıcı oluşturmak için

1. Yönetilen uygulamanız için projeyi açın.

2. **Proje** menüsünde **tüm dosyaları göster**' e tıklayın.

3. **Proje** menüsünde, **Başvuru Ekle**' ye tıklayın.

4. Başvuru Ekle iletişim kutusunda, **com** sekmesine tıklayın, kullanmak istediğiniz bileşeni seçin ve **Tamam**' a tıklayın.

     **Çözüm Gezgini**, com bileşeninin projenizdeki başvurular klasörüne eklendiğini unutmayın.

Artık COM nesnesine erişmek için kod yazabilirsiniz. Nesnesini bildirerek, Visual Basic için bir `Imports` ifadesiyle veya için C#bir `Using` bildirimiyle başlayabilirsiniz.

> [!NOTE]
> Microsoft Office bileşenleri programlamak istiyorsanız, önce Microsoft Indirme merkezi 'nden [Microsoft Office birincil birlikte çalışma derlemelerini](https://go.microsoft.com/fwlink/?LinkId=50479) (PIA) yükleyin. 4\. adımda, **Microsoft Word 11,0 nesne kitaplığı**gibi istediğiniz Office ürünü için uygun nesne kitaplığının en son sürümünü seçin.  
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a>.NET Framework araçlarını kullanarak bir çalışma zamanı çağrılabilir sarmalayıcı oluşturmak için  
  
- [Tlbimp. exe (tür kitaplığı Içeri Aktarıcı)](../tools/tlbimp-exe-type-library-importer.md) aracını çalıştırın.  
  
 Bu araç, özgün tür kitaplığında tanımlanan türler için çalışma zamanı meta verilerini içeren bir derleme oluşturur.  
  
## <a name="wrap-managed-objects-in-a-native-application"></a>Yönetilen nesneleri yerel bir uygulamada sarın  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a>Visual Studio kullanarak COM çağrılabilir bir sarmalayıcı oluşturmak için  
  
1. Yerel kodda çalıştırmak istediğiniz yönetilen sınıf için bir sınıf kitaplığı projesi oluşturun. Sınıf parametresiz bir oluşturucuya sahip olmalıdır.  
  
     AssemblyInfo dosyasında derlemelerinizin dört bölümden oluşan tam bir sürüm numarasına sahip olduğunuzu doğrulayın. Bu sayı, Windows kayıt defterinde sürüm oluşturmayı sürdürmek için gereklidir. Sürüm numaraları hakkında daha fazla bilgi için bkz. [derleme sürümü oluşturma](../../standard/assembly/versioning.md).  
  
2. **Proje** menüsünde **Özellikler**' e tıklayın.  
  
3. **Derle** sekmesine tıklayın.  
  
4. **Com birlikte çalışması Için kaydol** onay kutusunu seçin.  
  
 Projeyi derlediğinizde, derleme otomatik olarak COM birlikte çalışma için kaydedilir. Visual Studio 2005 ' de yerel bir uygulama oluşturuyorsanız, **Proje** menüsünde **Başvuru Ekle** ' ye tıklayarak derlemeyi kullanabilirsiniz.  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a>.NET Framework araçlarını kullanarak COM çağrılabilir bir sarmalayıcı oluşturmak için  
  
[Regasm. exe (derleme kayıt aracı)](../tools/regasm-exe-assembly-registration-tool.md) aracını çalıştırın.  
  
Bu araç derleme meta verilerini okur ve gerekli girdileri kayıt defterine ekler. Sonuç olarak, COM istemcileri .NET Framework sınıfları saydam şekilde oluşturabilir. Derlemeyi yerel bir COM sınıfı gibi kullanabilirsiniz.  
  
Herhangi bir dizinde bulunan bir derlemede Regasm. exe ' yi çalıştırabilir ve ardından [Gacutil. exe ' yi (genel bütünleştirilmiş kod önbelleği aracı)](../tools/gacutil-exe-gac-tool.md) çalıştırarak genel derleme önbelleğine taşıyabilirsiniz. Derlemenin taşınması konum kayıt defteri girdilerini geçersiz kılmaz, çünkü derleme başka bir yerde bulunmazsa genel derleme önbelleği her zaman incelenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanında Çağrılabilir Sarmalayıcı](../../standard/native-interop/runtime-callable-wrapper.md)
- [COM Çağrılabilir Sarmalayıcısı](../../standard/native-interop/com-callable-wrapper.md)
