---
title: Özel günlük dinleyicileri (Visual Basic) oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 07c13d22235f1198188d26122c137db1d91e64e8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342470"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>İzlenecek yol: Özel günlük dinleyicileri (Visual Basic) oluşturma
Bu kılavuzda, özel günlük dinleyiciyi oluşturun ve çıkışına dinleyecek şekilde yapılandırma gösterilmiştir `My.Application.Log` nesne.  
  
## <a name="getting-started"></a>Başlarken  
 Günlük dinleyicileri devralmalıdır <xref:System.Diagnostics.TraceListener> sınıfı.  
  
#### <a name="to-create-the-listener"></a>Dinleyici oluşturmak için  
  
-   Uygulamanızda adlı bir sınıf oluşturun `SimpleListener` öğesinden devralan <xref:System.Diagnostics.TraceListener>.  
  
     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]  
  
     <xref:System.Diagnostics.TraceListener.Write%2A> Ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> taban sınıfı tarafından gerekli yöntemleri çağırmak `MsgBox` kendi girişlerini görüntülemek için.  
  
     <xref:System.Security.Permissions.HostProtectionAttribute> Özniteliği uygulandığı <xref:System.Diagnostics.TraceListener.Write%2A> ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> yöntemleri taban sınıf yöntemlerini özniteliklerinin eşleşen böylece. <xref:System.Security.Permissions.HostProtectionAttribute> Özniteliği kod konak koruma eşitleme sunan belirlemek için kod çalıştıran konak sağlar.  
  
    > [!NOTE]
    >  <xref:System.Security.Permissions.HostProtectionAttribute> Özniteliktir yönetilmeyen uygulamalar yalnızca ortak dil çalışma zamanı konak ve konak koruması, SQL Server gibi uygulama üzerinde etkili.  
  
 Emin olmak için `My.Application.Log` günlük dinleyicinize kullanan kesin günlük dinleyicinize içeren derlemenin adı.  
  
 Sonraki yordamda, günlük dinleyici kesin adlandırılmış bütünleştirilmiş kod oluşturmak için gerekli olan basit adımlarda sağlar. Daha fazla bilgi için [bkz](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a>Dinleyici günlük derleme kesin adlandırmak için  
  
1. Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde seçin **özellikleri**.   
  
2. Tıklayın **imzalama** sekmesi.  
  
3. Seçin **derlemeyi imzalamayı** kutusu.  
  
4. Seçin  **\<yeni >** gelen **bir tanımlayıcı ad anahtar dosyası seç** aşağı açılan listesi.  
  
     **Katı ad anahtarı oluştur** iletişim kutusu açılır.  
  
5. Anahtar dosyasında için bir ad sağlayın **anahtar dosya adı** kutusu.  
  
6. Bir parolayı girin **parola gir** ve **parolayı onayla** kutuları.  
  
7. **Tamam**'ı tıklatın.  
  
8. Uygulamayı yeniden oluşturun.  
  
## <a name="adding-the-listener"></a>Dinleyici ekleme  
 Derlemeyi tanımlayıcı bir ada sahip, güçlü dinleyicisinin adını belirlemek gereken şekilde `My.Application.Log` günlük dinleyicinize kullanır.  
  
 Kesin adlandırılmış tür biçimi aşağıdaki gibidir.  
  
 \<tür adı >, \<derleme adı >, \<sürüm numarası >, \<kültür >, \<tanımlayıcı ad >  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a>Dinleyici güçlü adını belirlemek için  
  
-   Aşağıdaki kod, kesin adlandırılmış tür adını belirlemek gösterilmektedir `SimpleListener`.  
  
     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]  
  
     Tür tanımlayıcı adı projenize bağlıdır.  
  
 Tanımlayıcı ad ile dinleyiciye ekleyebilirsiniz `My.Application.Log` dinleyici günlük koleksiyonu.  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a>My.Application.Log için dinleyici eklemek için  
  
1. App.config dosyasında sağ **Çözüm Gezgini** ve **açık**.  
  
     -veya-  
  
     Bir app.config dosyası varsa:  
  
    1.  Üzerinde **proje** menüsünde seçin **Yeni Öğe Ekle**.  
  
    2.  Gelen **Yeni Öğe Ekle** iletişim kutusunda **uygulama yapılandırma dosyası**.  
  
    3.  **Ekle**'yi tıklatın.  
  
2. Bulun `<listeners>` bölümünde `<source>` ile bölümünde `name` "DefaultSource bulunan", öznitelik `<sources>` bölümü. `<sources>` Bölümünde bulunan `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
3. Bu öğeye eklemek `<listeners>` bölümü:  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4. Bulun `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
5. Bu öğe ekleyen `<sharedListeners>` bölümü:  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     Değiştirin `SimpleLogStrongName` dinleyici tanımlayıcı adı olarak.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl yapılır: Özel Durumları Günlüğe Kaydetme](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Nasıl yapılır: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
