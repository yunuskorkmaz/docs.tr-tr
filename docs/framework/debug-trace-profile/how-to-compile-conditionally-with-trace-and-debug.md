---
title: "Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f3907888ebcda9c5c6c498cbff39956391f7e213
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a>Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme
Uygulama geliştirme sırasında hata ayıklarken, Visual Studio çıktı penceresinde, izleme ve hata ayıklama çıkışını gidin. Ancak, dağıtılan bir uygulama izleme özellikleri içerecek şekilde, Araçlı uygulamalarınızla derleme gerekir **izleme** etkin derleyici yönergesi. Bu, uygulamanızın yayın sürümüne derlenecek izleme kodu sağlar. Değil etkinleştirirseniz, **izleme** yönerge, tüm izleme kodu derleme sırasında yok sayılır ve dağıtacağınız yürütülebilir kod dahil edilmez.  
  
 İzleme ve hata ayıklama yöntemleri koşullu öznitelikler ilişkilendirdiniz. Örneğin, için koşullu öznitelik izleme ise **true**, tüm izleme deyimleri, bir derlemede (bir derlenmiş .exe veya .dll); dahil edilen **izleme** koşullu özniteliktir **yanlış**, izleme deyimleri dahil edilmez.  
  
 Ya da sahip **izleme** veya **hata ayıklama** bir yapı veya her ikisi de ya da hiçbiri için koşullu öznitelik açık. Bu nedenle, yapı dört tür vardır: **hata ayıklama**, **izleme**, her iki ya da hiçbiri. Bazı yayın derlemeleri Üretim dağıtımı için ne içerebilir; en hata ayıklama derlemeleri her ikisi de içerir.  
  
 Uygulamanızın çeşitli şekillerde derleyici ayarları belirtin:  
  
-   Özellik sayfaları  
  
-   Komut satırı  
  
-   **#CONST** (Visual Basic için) ve **#define** için (C#)  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a>Özellik sayfaları iletişim kutusundan derleme ayarlarını değiştirmek için  
  
1.  Proje düğümüne sağ tıklayın **Çözüm Gezgini**.  
  
2.  Seçin **özellikleri** kısayol menüsünden.  
  
    -   Visual Basic'te tıklatın **derleme** özellik sayfasının sol bölmesindeki sekmesine ve ardından **Gelişmiş derleme seçenekleri** görüntülemek için düğmesini **Gelişmiş derleyici ayarları**iletişim kutusu. Etkinleştirmek istediğiniz derleyici ayarları için onay kutularını seçin. Devre dışı bırakmak istediğiniz ayarları için onay kutularını temizleyin.  
  
    -   C# ' ta tıklayın **yapı** özellik sayfasının sol bölmesindeki sekmesine ve ardından etkinleştirmek istediğiniz derleyici ayarları için onay kutularını seçin. Devre dışı bırakmak istediğiniz ayarları için onay kutularını temizleyin.  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a>Komut satırını kullanarak Araçlı Kodu derlemek için  
  
1.  Koşullu derleme anahtar komut satırında ayarlayın. Derleyici izleme dahil veya yürütülebilir dosya kodda hata ayıklama.  
  
     Örneğin, komut satırına girilen aşağıdaki derleyici yönergeleri izleme kodunuzu derlenmiş bir yürütülebilir dosya içerir:  
  
     Visual Basic: **vbc /r:System.dll /d:TRACE TRUE /d:DEBUG = FALSE MyApplication.vb =**  
  
     C# ' ta: **csc /r:System.dll /d:TRACE /d:DEBUG FALSE MyApplication.cs =**  
  
    > [!TIP]
    >  Birden fazla uygulama dosyasını derleyin, dosya adları arasında Örneğin, bir boşluk bırakın **MyApplication1.vb MyApplication2.vb MyApplication3.vb** veya **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.  
  
     Yukarıdaki örneklerde kullanılan koşullu derleme yönergeleri anlamını aşağıdaki gibidir:  
  
    |Yönergesi|Açıklama|  
    |---------------|-------------|  
    |`vbc`|Visual Basic derleyici|  
    |`csc`|C# Derleyici|  
    |`/r:`|Dış bir derlemeye (EXE ya da DLL) başvurur|  
    |`/d:`|Koşullu derleme simgesi tanımlar|  
  
    > [!NOTE]
    >  İzleme yazım veya büyük harfler ile hata ayıklama. Koşullu derleme komutları hakkında daha fazla bilgi için girin `vbc /?` (Visual Basic için) veya `csc /?` (C# için) komut isteminde. Daha fazla bilgi için bkz: [komut satırından derleme](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) veya [komut satırı derleyicisini çağırma](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a>Koşullu derleme kullanarak gerçekleştirmek için #CONST veya #define  
  
1.  Programlama diliniz için uygun deyimi kaynak kodu dosyasının üst kısmında yazın.  
  
    |Dil|Deyim|Sonuç|  
    |--------------|---------------|------------|  
    |**Visual Basic**|**#CONST izleme = true**|İzlemeyi etkinleştirir|  
    ||**#CONST izleme = false**|İzleme devre dışı bırakır|  
    ||**#CONST DEBUG = true**|Hata ayıklamayı etkinleştirir|  
    ||**#CONST DEBUG = false**|Hata ayıklama devre dışı bırakır|  
    |**C#**|**# İzleme define**|İzlemeyi etkinleştirir|  
    ||**#undef izleme**|İzleme devre dışı bırakır|  
    ||**# hata ayıklama define**|Hata ayıklamayı etkinleştirir|  
    ||**#undef hata ayıklama**|Hata ayıklama devre dışı bırakır|  
  
### <a name="to-disable-tracing-or-debugging"></a>İzleme veya hata ayıklama devre dışı bırakmak için  
  
1.  Derleyici yönergesi kaynak kodunuzdan silin.  
  
     \-veya -  
  
2.  Out derleyici yönergesi açıklama.  
  
    > [!NOTE]
    >  Derlemek hazır olduğunuzda, ya da seçebilirsiniz **yapı** gelen **yapı** menüsünde veya komut satırı yöntemini kullanır ancak olmadan yazarak **d:** koşullu tanımlamak için derleme simgeler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme ve uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [Nasıl yapılır: oluşturma ve başlatma izleme anahtarları](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)  
 [İzleme anahtarları](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [İzleme dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [Nasıl yapılır: uygulama koduna izleme deyimleri ekleme](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [Nasıl yapılır: Visual Studio komut satırı için ortam değişkenlerini ayarlama](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 [Nasıl yapılır: komut satırı derleyicisini çağırma](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)
