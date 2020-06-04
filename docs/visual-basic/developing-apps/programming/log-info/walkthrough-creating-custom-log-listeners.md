---
title: Özel Günlük Dinleyicileri Oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 5a140607a4fe7e1e13de54e8d56cab53e52aaa2a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398272"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a>İzlenecek Yol: Özel Günlük Dinleyicileri Oluşturma (Visual Basic)

Bu izlenecek yol, özel bir günlük dinleyicisinin nasıl oluşturulacağını ve nesnenin çıkışını dinlemek için nasıl yapılandırılacağını gösterir `My.Application.Log` .

## <a name="getting-started"></a>Başlarken

Günlük dinleyicileri sınıfından devralması gerekir <xref:System.Diagnostics.TraceListener> .

#### <a name="to-create-the-listener"></a>Dinleyiciyi oluşturmak için

- Uygulamanızda öğesinden devralan adlı bir sınıf oluşturun `SimpleListener` <xref:System.Diagnostics.TraceListener> .

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     <xref:System.Diagnostics.TraceListener.Write%2A> <xref:System.Diagnostics.TraceListener.WriteLine%2A> Temel sınıf için gereken ve yöntemleri, `MsgBox` girişini göstermek için çağırır.

     <xref:System.Security.Permissions.HostProtectionAttribute>Özniteliği <xref:System.Diagnostics.TraceListener.Write%2A> ve <xref:System.Diagnostics.TraceListener.WriteLine%2A> yöntemlerine, özniteliklerinin temel sınıf yöntemleriyle eşleşecek şekilde uygulanır. <xref:System.Security.Permissions.HostProtectionAttribute>Özniteliği kodu çalıştıran konağın, kodun konak koruma eşitlemesini gösterir olduğunu belirlemesini sağlar.

    > [!NOTE]
    > <xref:System.Security.Permissions.HostProtectionAttribute>Özniteliği yalnızca ortak dil çalışma zamanını barındıran yönetilmeyen uygulamalarda etkilidir ve SQL Server gibi konak korumasını uygular.

`My.Application.Log`Günlük dinleyicinizi kullandığından emin olmak için, günlük dinleyicinizi içeren derlemeyi kesin bir şekilde adlandırın.

Sonraki yordam, kesin adlandırılmış bir log-Listener derlemesi oluşturmak için bazı basit adımlar sağlar. Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../../standard/assembly/create-use-strong-named.md).

#### <a name="to-strongly-name-the-log-listener-assembly"></a>Log dinleyicisi derlemesini kesin olarak adlandırmak için

1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' i seçin.

2. **İmzalama** sekmesine tıklayın.

3. **Derlemeyi imzala** kutusunu seçin.

4. **\<New>** **Tanımlayıcı ad anahtar dosyası seçin** aşağı açılan listesinden seçim yapın.

     **Tanımlayıcı ad anahtarı oluştur** iletişim kutusu açılır.

5. Anahtar dosya **adı** kutusuna anahtar dosyası için bir ad girin.

6. Parolayı **gir** ve **Parolayı Onayla** kutularına bir parola girin.

7. **Tamam**'a tıklayın.

8. Uygulamayı yeniden derleyin.

## <a name="adding-the-listener"></a>Dinleyiciyi ekleme

Artık derlemenin tanımlayıcı bir adı olduğuna göre, günlük dinleyicinizi kullanması için dinleyicinin tanımlayıcı adını belirlemeniz gerekir `My.Application.Log` .

Kesin adlandırılmış türün biçimi aşağıdaki gibidir.

\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name>

#### <a name="to-determine-the-strong-name-of-the-listener"></a>Dinleyicinin tanımlayıcı adını belirleme

- Aşağıdaki kod, için kesin adlandırılmış tür adının nasıl belirleneceğini göstermektedir `SimpleListener` .

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     Türün tanımlayıcı adı projenize bağlıdır.

Tanımlayıcı adıyla, dinleyiciyi `My.Application.Log` log-Listener koleksiyonuna ekleyebilirsiniz.

#### <a name="to-add-the-listener-to-myapplicationlog"></a>Dinleyiciyi My. Application. log dosyasına eklemek için

1. **Çözüm Gezgini** App. config dosyasına sağ tıklayın ve **Aç**' ı seçin.

     -veya-

     Bir App. config dosyası varsa:

    1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

    2. **Yeni öğe Ekle** Iletişim kutusundan **uygulama yapılandırma dosyası**' nı seçin.

    3. **Ekle**'ye tıklayın.

2. Bölümünde `<listeners>` `<source>` `name` yer alan "DefaultSource" özniteliğine sahip bölümünde bölümünü bulun `<sources>` . Bölümü, bölümünde `<sources>` `<system.diagnostics>` , üst düzey `<configuration>` bölümünde bulunur.

3. Bu öğeyi `<listeners>` bölümüne ekleyin:

    ```xml
    <add name="SimpleLog" />
    ```

4. Bölümünde, `<sharedListeners>` üst düzey bölümünde bölümünde bulunan bölümünü bulun `<system.diagnostics>` `<configuration>` .

5. Bu öğeyi bu bölüme ekleyin `<sharedListeners>` :

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     Değerini `SimpleLogStrongName` dinleyicinin tanımlayıcı adı olacak şekilde değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [Uygulama Günlükleriyle Çalışma](working-with-application-logs.md)
- [Nasıl yapılır: Özel Durumları Günlüğe Kaydetme](how-to-log-exceptions.md)
- [Nasıl yapılır: Günlük İletileri Yazma](how-to-write-log-messages.md)
- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](walkthrough-changing-where-my-application-log-writes-information.md)
