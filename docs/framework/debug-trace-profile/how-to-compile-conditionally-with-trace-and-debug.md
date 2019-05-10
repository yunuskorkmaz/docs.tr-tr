---
title: 'Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme'
ms.date: 03/30/2017
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9b60cdef2af25ce712fcb2401b7f776d3add5b5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64660407"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a>Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme
Uygulama geliştirme sırasında hata ayıklama sırasında Visual Studio çıktı penceresinde, izleme ve hata ayıklama çıkışını gidin. Ancak, dağıtılan bir uygulamada İzleme özelliklerini eklemek için Araçlı uygulamalarınızla derlemelisiniz **izleme** etkin derleyici yönergesi. Bu, uygulamanızın yayın sürümüne derlenecek izleme kodu sağlar. Değil etkinleştirirseniz **izleme** yönergesi, tüm izleme kodu derleme sırasında yok sayılır ve dağıtacağınız yürütülebilir kodu bulunmaz.  
  
 Koşullu öznitelikler, izleme ve hata ayıklama yöntemleri ilişkilendirdiniz. Örneğin, koşul özniteliğini izleme ise **true**, tüm izleme deyimleri (derlenmiş .exe dosyasının veya .dll); bir derlemenin içinde dahil edilir **izleme** conditional özniteliği olduğundan **false**, izleme deyimleri dahil edilmez.  
  
 Ya da sahip **izleme** veya **hata ayıklama** conditional özniteliği açık olarak bir derleme veya her ikisini ya da hiçbiri için. Bu nedenle, bir derleme dört tür vardır: **Hata ayıklama**, **izleme**, her iki ya da hiçbiri. Bazı derleme yapıları Üretim dağıtımı için ne içerebilir; Çoğu hata ayıklama yapıları her ikisi de içerir.  
  
 Uygulamanız çeşitli şekillerde için derleyici ayarlarını belirtebilirsiniz:  
  
- Özellik sayfaları  
  
- Komut satırı  
  
- **#CONST** (Visual Basic için) ve **#define** (için C#)  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a>Özellik sayfaları iletişim kutusundan derleme ayarlarını değiştirmek için  
  
1. ' Nde proje düğümüne sağ **Çözüm Gezgini**.  
  
2. Seçin **özellikleri** kısayol menüsünden.  
  
    - Visual Basic'te tıklayın **derleme** özellik sayfasının sol bölmede sekme'a tıklayın **Gelişmiş derleme seçenekleri** görüntülemek için düğmeyi **Gelişmiş derleyici ayarları**iletişim kutusu. Etkinleştirmek istediğiniz derleyici ayarları için onay kutularını seçin. Devre dışı bırakmak istediğiniz ayarların onay kutularını temizleyin.  
  
    - İçinde C#, tıklayın **derleme** özellik sayfasının sol bölmede sekme ve etkinleştirmek istediğiniz derleyici ayarları için onay kutularını seçin. Devre dışı bırakmak istediğiniz ayarların onay kutularını temizleyin.  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a>Komut satırını kullanarak işaretlenmiş kod derlemek için  
  
1. Komut satırında bir koşullu derleyici anahtarını ayarlayın. Derleyici, izleme eklemek veya yürütülebilir kodu hatalarını ayıklama.  
  
     Örneğin, komut satırına girilen aşağıdaki derleyici yönergesi, izleme kodu derlenmiş bir yürütülebilir dosya şunlardır:  
  
     Visual Basic için: **vbc-r:System.dll -d: izleme = TRUE -d: hata ayıklama FALSE MyApplication.vb =**  
  
     İçin C#: **csc-r:System.dll -d: izleme -d: hata ayıklama FALSE MyApplication.cs =**  
  
    > [!TIP]
    >  Birden fazla uygulama dosyasını derlemek için dosya adları, örneğin, bir boşluk bırakın **MyApplication1.vb MyApplication2.vb MyApplication3.vb** veya **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.  
  
     Yukarıdaki örneklerde kullanılan koşullu derleme yönergeleri anlamını aşağıdaki gibidir:  
  
    |Yönergesi|Açıklama|  
    |---------------|-------------|  
    |`vbc`|Visual Basic derleyici|  
    |`csc`|C#Derleyici|  
    |`-r:`|Dış bütünleştirilmiş (EXE veya DLL) başvuruyor|  
    |`-d:`|Koşullu derleme sembolünü tanımlar|  
  
    > [!NOTE]
    >  İzleme yazım gerekir veya büyük harfler ile hata ayıklama. Koşullu derleme komutları hakkında daha fazla bilgi için girin `vbc /?` (için Visual Basic) veya `csc /?` (için C#) komut isteminde. Daha fazla bilgi için [komut satırından derleme](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) veya [komut satırı derleyicisini çağırma](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a>Koşullu derleme kullanarak gerçekleştirmek için #CONST veya #define  
  
1. Programlama diliniz için uygun deyim kaynak kod dosyasının en üstüne yazın.  
  
    |Dil|Deyim|Sonuç|  
    |--------------|---------------|------------|  
    |**Visual Basic**|**#CONST izleme = true**|İzleme sağlar|  
    ||**#CONST izleme = false**|İzleme devre dışı bırakır|  
    ||**#CONST hata ayıklama = true**|Hata ayıklamayı etkinleştirir|  
    ||**#CONST DEBUG = false**|Hata ayıklama devre dışı bırakır|  
    |**C#**|**#define TRACE**|İzleme sağlar|  
    ||**#undef izleme**|İzleme devre dışı bırakır|  
    ||**#define hata ayıklama**|Hata ayıklamayı etkinleştirir|  
    ||**#undef hata ayıklama**|Hata ayıklama devre dışı bırakır|  
  
### <a name="to-disable-tracing-or-debugging"></a>İzleme veya hata ayıklama devre dışı bırakmak için  
  
Derleyici yönergesi, kaynak kodunuzdan silin.  
  
\- veya -  
  
Out derleyici yönergesi yorum.  
  
> [!NOTE]
>  Derlemek hazır olduğunuzda ya da seçebilirsiniz **derleme** gelen **derleme** menüsünden veya komut satırı yöntemini kullanın ancak yazmayı olmadan **d:** koşullu tanımlamak için derleme simgeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme ve İşaretleme Uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [Nasıl yapılır: Oluşturma, başlatma ve izleme anahtarları yapılandırma](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [İzleme Anahtarları](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [İzleme Dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [Nasıl yapılır: Uygulama koduna izleme deyimleri ekleme](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [Nasıl yapılır: Visual Studio komut satırı için ortam değişkenlerini ayarlama](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [Nasıl yapılır: Komut Satırı Derleyicisini Çağırma](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
