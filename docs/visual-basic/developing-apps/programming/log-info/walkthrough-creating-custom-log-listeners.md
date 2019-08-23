---
title: Özel günlük dinleyicileri oluşturma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 90135074a4d34ea73743faffb2531305fcb326fb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965269"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>İzlenecek yol: Özel günlük dinleyicileri oluşturma (Visual Basic)
Bu izlenecek yol, özel bir günlük dinleyicisinin nasıl oluşturulacağını ve `My.Application.Log` nesnenin çıkışını dinlemek için nasıl yapılandırılacağını gösterir.  
  
## <a name="getting-started"></a>Başlarken  
 Günlük dinleyicileri <xref:System.Diagnostics.TraceListener> sınıfından devralması gerekir.  
  
#### <a name="to-create-the-listener"></a>Dinleyiciyi oluşturmak için  
  
- Uygulamanızda öğesinden `SimpleListener` <xref:System.Diagnostics.TraceListener>devralan adlı bir sınıf oluşturun.  
  
     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]  
  
     Temel sınıf <xref:System.Diagnostics.TraceListener.WriteLine%2A> için gereken `MsgBox` ve yöntemleri, girişini göstermek için çağırır. <xref:System.Diagnostics.TraceListener.Write%2A>  
  
     <xref:System.Security.Permissions.HostProtectionAttribute> Özniteliği <xref:System.Diagnostics.TraceListener.Write%2A> ve yöntemlerine<xref:System.Diagnostics.TraceListener.WriteLine%2A> , özniteliklerinin temel sınıf yöntemleriyle eşleşecek şekilde uygulanır. <xref:System.Security.Permissions.HostProtectionAttribute> Özniteliği kodu çalıştıran konağın, kodun konak koruma eşitlemesini gösterir olduğunu belirlemesini sağlar.  
  
    > [!NOTE]
    > <xref:System.Security.Permissions.HostProtectionAttribute> Özniteliği yalnızca ortak dil çalışma zamanını barındıran yönetilmeyen uygulamalarda etkilidir ve SQL Server gibi konak korumasını uygular.  
  
 Günlük dinleyicinizi `My.Application.Log` kullandığından emin olmak için, günlük dinleyicinizi içeren derlemeyi kesin bir şekilde adlandırın.  
  
 Sonraki yordam, kesin adlandırılmış bir log-Listener derlemesi oluşturmak için bazı basit adımlar sağlar. Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a>Log dinleyicisi derlemesini kesin olarak adlandırmak için  
  
1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' i seçin.   
  
2. **İmzalama** sekmesine tıklayın.  
  
3. **Derlemeyi imzala** kutusunu seçin.  
  
4. **Tanımlayıcı ad anahtar dosyası seçin** açılır listesinden  **\<yeni >** ' yi seçin.  
  
     **Tanımlayıcı ad anahtarı oluştur** iletişim kutusu açılır.  
  
5. Anahtar dosya **adı** kutusuna anahtar dosyası için bir ad girin.  
  
6. Parolayı **gir** ve **Parolayı Onayla** kutularına bir parola girin.  
  
7. **Tamam**'ı tıklatın.  
  
8. Uygulamayı yeniden derleyin.  
  
## <a name="adding-the-listener"></a>Dinleyiciyi ekleme  
 Artık derlemenin tanımlayıcı bir adı olduğuna göre, günlük dinleyicinizi `My.Application.Log` kullanması için dinleyicinin tanımlayıcı adını belirlemeniz gerekir.  
  
 Kesin adlandırılmış türün biçimi aşağıdaki gibidir.  
  
 \<tür adı >, \<derleme adı >, \<sürüm numarası >, \<Kültür >, \<tanımlayıcı ad >  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a>Dinleyicinin tanımlayıcı adını belirleme  
  
- Aşağıdaki kod, için `SimpleListener`kesin adlandırılmış tür adının nasıl belirleneceğini göstermektedir.  
  
     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]  
  
     Türün tanımlayıcı adı projenize bağlıdır.  
  
 Tanımlayıcı adıyla, dinleyiciyi `My.Application.Log` log-Listener koleksiyonuna ekleyebilirsiniz.  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a>Dinleyiciyi My. Application. log dosyasına eklemek için  
  
1. **Çözüm Gezgini** App. config dosyasına sağ tıklayın ve **Aç**' ı seçin.  
  
     -veya-  
  
     Bir App. config dosyası varsa:  
  
    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.  
  
    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.  
  
    3. **Ekle**'yi tıklatın.  
  
2. Bölümünde yer `name` alan "DefaultSource"özniteliğinesahipbölümündebölümünübulun`<sources>`. `<listeners>` `<source>` Bölümü, bölümünde, üst düzey `<system.diagnostics>` `<configuration>` bölümünde bulunur. `<sources>`  
  
3. Bu öğeyi `<listeners>` bölümüne ekleyin:  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4. Bölümünde, üst düzey `<system.diagnostics>` `<configuration>` bölümünde bölümünde bulunan bölümünübulun.`<sharedListeners>`  
  
5. Bu öğeyi `<sharedListeners>` bu bölüme ekleyin:  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     Değerini dinleyicinin tanımlayıcı adı `SimpleLogStrongName` olacak şekilde değiştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl yapılır: Günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Nasıl yapılır: Yazma günlüğü Iletileri](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [İzlenecek yol: My. Application. log dosyası yazma bilgilerini değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
