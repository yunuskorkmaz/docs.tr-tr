---
title: SendMail Özel Etkinliği
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: e7cc64e68c3d78b9ee7ec813700e96a52c239141
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182776"
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="34b68-102">SendMail Özel Etkinliği</span><span class="sxs-lookup"><span data-stu-id="34b68-102">SendMail Custom Activity</span></span>
<span data-ttu-id="34b68-103">Bu örnek, iş akışı uygulamasında kullanılmak üzere <xref:System.Activities.AsyncCodeActivity> SMTP kullanarak posta göndermekten türeyen özel bir etkinliğin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="34b68-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="34b68-104">Özel etkinlik, eşit olarak <xref:System.Net.Mail.SmtpClient> e-posta gönderme ve kimlik doğrulaması ile posta gönderme özelliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="34b68-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="34b68-105">Ayrıca test modu, belirteç değiştirme, dosya şablonları ve test bırakma yolu gibi bazı son kullanıcı özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="34b68-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="34b68-106">Aşağıdaki tabloda etkinlik için `SendMail` bağımsız değişkenler ayrıntılı olarak anlatılır.</span><span class="sxs-lookup"><span data-stu-id="34b68-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="34b68-107">Adı</span><span class="sxs-lookup"><span data-stu-id="34b68-107">Name</span></span>|<span data-ttu-id="34b68-108">Tür</span><span class="sxs-lookup"><span data-stu-id="34b68-108">Type</span></span>|<span data-ttu-id="34b68-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34b68-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="34b68-110">Host</span><span class="sxs-lookup"><span data-stu-id="34b68-110">Host</span></span>|<span data-ttu-id="34b68-111">Dize</span><span class="sxs-lookup"><span data-stu-id="34b68-111">String</span></span>|<span data-ttu-id="34b68-112">SMTP sunucu ana bilgisayarının adresi.</span><span class="sxs-lookup"><span data-stu-id="34b68-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="34b68-113">Bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="34b68-113">Port</span></span>|<span data-ttu-id="34b68-114">Dize</span><span class="sxs-lookup"><span data-stu-id="34b68-114">String</span></span>|<span data-ttu-id="34b68-115">SMTP hizmetinin ana bilgisayardaki bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="34b68-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="34b68-116">Etkinleştirssl</span><span class="sxs-lookup"><span data-stu-id="34b68-116">EnableSsl</span></span>|<span data-ttu-id="34b68-117">bool</span><span class="sxs-lookup"><span data-stu-id="34b68-117">bool</span></span>|<span data-ttu-id="34b68-118">Bağlantıyı şifrelemek <xref:System.Net.Mail.SmtpClient> için Güvenli Soket katmanının (SSL) kullanılıp kullanılmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="34b68-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="34b68-119">UserName</span><span class="sxs-lookup"><span data-stu-id="34b68-119">UserName</span></span>|<span data-ttu-id="34b68-120">Dize</span><span class="sxs-lookup"><span data-stu-id="34b68-120">String</span></span>|<span data-ttu-id="34b68-121">Gönderen <xref:System.Net.Mail.SmtpClient.Credentials%2A> özelliğinin kimliğini doğrulamak için kimlik bilgilerini ayarlamak için kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="34b68-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="34b68-122">Parola</span><span class="sxs-lookup"><span data-stu-id="34b68-122">Password</span></span>|<span data-ttu-id="34b68-123">Dize</span><span class="sxs-lookup"><span data-stu-id="34b68-123">String</span></span>|<span data-ttu-id="34b68-124">Gönderen <xref:System.Net.Mail.SmtpClient.Credentials%2A> özelliğinin kimliğini doğrulamak için kimlik bilgilerini ayarlamak için parola.</span><span class="sxs-lookup"><span data-stu-id="34b68-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="34b68-125">Özne</span><span class="sxs-lookup"><span data-stu-id="34b68-125">Subject</span></span>|<span data-ttu-id="34b68-126"><xref:System.Activities.InArgument%601>\<dize></span><span class="sxs-lookup"><span data-stu-id="34b68-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="34b68-127">İletinin konusu.</span><span class="sxs-lookup"><span data-stu-id="34b68-127">Subject of the message.</span></span>|  
|<span data-ttu-id="34b68-128">Gövde</span><span class="sxs-lookup"><span data-stu-id="34b68-128">Body</span></span>|<span data-ttu-id="34b68-129"><xref:System.Activities.InArgument%601>\<dize></span><span class="sxs-lookup"><span data-stu-id="34b68-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="34b68-130">Mesajın gövdesi.</span><span class="sxs-lookup"><span data-stu-id="34b68-130">Body of the message.</span></span>|  
|<span data-ttu-id="34b68-131">Ekler</span><span class="sxs-lookup"><span data-stu-id="34b68-131">Attachments</span></span>|<span data-ttu-id="34b68-132"><xref:System.Activities.InArgument%601>\<dize></span><span class="sxs-lookup"><span data-stu-id="34b68-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="34b68-133">Bu e-posta iletisine bağlı verileri depolamak için kullanılan ek koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="34b68-133">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="34b68-134">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="34b68-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="34b68-135">Bu e-posta iletisi için adresten.</span><span class="sxs-lookup"><span data-stu-id="34b68-135">From address for this email message.</span></span>|  
|<span data-ttu-id="34b68-136">Alıcı</span><span class="sxs-lookup"><span data-stu-id="34b68-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="34b68-137">Bu e-posta iletisinin alıcılarını içeren adres koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="34b68-137">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="34b68-138">CC</span><span class="sxs-lookup"><span data-stu-id="34b68-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="34b68-139">Bu e-posta iletisi için karbon kopya (CC) alıcıları içeren adres toplama.</span><span class="sxs-lookup"><span data-stu-id="34b68-139">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="34b68-140">Gizli</span><span class="sxs-lookup"><span data-stu-id="34b68-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="34b68-141">Bu e-posta iletisi için kör karbon kopya (BCC) alıcıları içeren adres toplama.</span><span class="sxs-lookup"><span data-stu-id="34b68-141">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="34b68-142">Belirteçler</span><span class="sxs-lookup"><span data-stu-id="34b68-142">Tokens</span></span>|<span data-ttu-id="34b68-143"><xref:System.Activities.InArgument%601><IDictionary\<dize, dize>></span><span class="sxs-lookup"><span data-stu-id="34b68-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="34b68-144">Vücutta değiştirilecek belirteçler.</span><span class="sxs-lookup"><span data-stu-id="34b68-144">Tokens to replace in the body.</span></span> <span data-ttu-id="34b68-145">Bu özellik, kullanıcıların daha sonra bu özelliği kullanılarak sağlanan belirteçleri ile değiştirilebilir daha gövdede bazı değerleri belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="34b68-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="34b68-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="34b68-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="34b68-147">Dize</span><span class="sxs-lookup"><span data-stu-id="34b68-147">String</span></span>|<span data-ttu-id="34b68-148">Gövde için bir şablonyolu.</span><span class="sxs-lookup"><span data-stu-id="34b68-148">Path of a template for the body.</span></span> <span data-ttu-id="34b68-149">Etkinlik, `SendMail` bu dosyanın içeriğini gövde özelliğine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="34b68-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="34b68-150">Şablon belirteçleri özelliğinin içeriği ile değiştirilen belirteçleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="34b68-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="34b68-151">Testmailto</span><span class="sxs-lookup"><span data-stu-id="34b68-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="34b68-152">Bu özellik ayarlandığında, tüm e-postalar içinde belirtilen adrese gönderilir.</span><span class="sxs-lookup"><span data-stu-id="34b68-152">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="34b68-153">Bu özellik, iş akışlarını sınarken kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="34b68-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="34b68-154">Örneğin, tüm e-postaların gerçek alıcılara gönderilmeden gönderildiğinden emin olmak istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="34b68-154">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="34b68-155">TestDroppath</span><span class="sxs-lookup"><span data-stu-id="34b68-155">TestDropPath</span></span>|<span data-ttu-id="34b68-156">Dize</span><span class="sxs-lookup"><span data-stu-id="34b68-156">String</span></span>|<span data-ttu-id="34b68-157">Bu özellik ayarlandığında, tüm e-postalar da belirtilen dosyaya kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="34b68-157">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="34b68-158">Bu özellik, giden e-postaların biçiminin ve içeriğinin uygun olduğundan emin olmak için iş akışlarını test ederken veya hata ayıklarken kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="34b68-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="34b68-159">Çözüm İçeriği</span><span class="sxs-lookup"><span data-stu-id="34b68-159">Solution Contents</span></span>  
 <span data-ttu-id="34b68-160">Çözüm iki proje içerir.</span><span class="sxs-lookup"><span data-stu-id="34b68-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="34b68-161">Project</span><span class="sxs-lookup"><span data-stu-id="34b68-161">Project</span></span>|<span data-ttu-id="34b68-162">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34b68-162">Description</span></span>|<span data-ttu-id="34b68-163">Önemli Dosyalar</span><span class="sxs-lookup"><span data-stu-id="34b68-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="34b68-164">Sendmail</span><span class="sxs-lookup"><span data-stu-id="34b68-164">SendMail</span></span>|<span data-ttu-id="34b68-165">SendMail etkinliği</span><span class="sxs-lookup"><span data-stu-id="34b68-165">The SendMail activity</span></span>|<span data-ttu-id="34b68-166">1. SendMail.cs: ana faaliyet için uygulama</span><span class="sxs-lookup"><span data-stu-id="34b68-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="34b68-167">2. SendMailDesigner.xaml ve SendMailDesigner.xaml.cs: SendMail etkinliği için tasarımcı</span><span class="sxs-lookup"><span data-stu-id="34b68-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="34b68-168">3. MailTemplateBody.htm: e-postanın gönderilmesi için şablon.</span><span class="sxs-lookup"><span data-stu-id="34b68-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="34b68-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="34b68-169">SendMailTestClient</span></span>|<span data-ttu-id="34b68-170">SendMail etkinliğini test etmek için istemci.</span><span class="sxs-lookup"><span data-stu-id="34b68-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="34b68-171">Bu proje, SendMail etkinliğini çağırmak için iki yol gösterir: bildirimsel ve programsal olarak.</span><span class="sxs-lookup"><span data-stu-id="34b68-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="34b68-172">1. Sequence1.xaml: SendMail etkinliğini çağıran iş akışı.</span><span class="sxs-lookup"><span data-stu-id="34b68-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="34b68-173">2. Program.cs: Sequence1 çağırır ve aynı zamanda SendMail kullanan bir iş akışı programlı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="34b68-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="34b68-174">SendMail etkinliğinin daha fazla yapılandırması</span><span class="sxs-lookup"><span data-stu-id="34b68-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="34b68-175">Örnekte gösterilmese de, kullanıcılar SendMail etkinliğinin ek yapılandırmasını gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="34b68-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="34b68-176">Sonraki üç bölüm bunun nasıl yapıldığını gösteriyor.</span><span class="sxs-lookup"><span data-stu-id="34b68-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="34b68-177">Vücutta belirtilen belirteçleri kullanarak e-posta gönderme</span><span class="sxs-lookup"><span data-stu-id="34b68-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="34b68-178">Bu kod snippet vücutta belirteçleri ile e-posta gönderebilirsiniz nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="34b68-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="34b68-179">Jetonların gövde mülkünde nasıl sağlandığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="34b68-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="34b68-180">Bu belirteçler için değerler belirteçleri özelliğine sağlanır.</span><span class="sxs-lookup"><span data-stu-id="34b68-180">Values for those tokens are provided to the tokens property.</span></span>  
  
```csharp  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="34b68-181">Şablon kullanarak e-posta gönderme</span><span class="sxs-lookup"><span data-stu-id="34b68-181">Sending an email using a template</span></span>  
 <span data-ttu-id="34b68-182">Bu parçacık, vücuttaki şablon belirteçlerini kullanarak e-postanın nasıl gönderilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="34b68-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="34b68-183">`BodyTemplateFilePath` Özelliği ayarlarken Gövde özelliği nin değerini sağlamamıza gerek olmadığını unutmayın (şablon dosyasının içeriği gövdeye kopyalanır).</span><span class="sxs-lookup"><span data-stu-id="34b68-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
```csharp  
new SendMail  
{
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="34b68-184">Test Modunda Posta Gönderme</span><span class="sxs-lookup"><span data-stu-id="34b68-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="34b68-185">Bu kod snippet iki test özellikleri ayarlamak `TestMailTo` için nasıl gösterir: tüm `john.doe@contoso.con` iletileri ayarlayarak (To, Cc, Bcc değerleri ne olursa olsun) gönderilecektir.</span><span class="sxs-lookup"><span data-stu-id="34b68-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="34b68-186">TestDropPath ayarlayarak tüm giden e-postalar da sağlanan yolda kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="34b68-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="34b68-187">Bu özellikler bağımsız olarak ayarlanabilir (bunlar ilişkili değildir).</span><span class="sxs-lookup"><span data-stu-id="34b68-187">These properties can be set independently (they are not related).</span></span>  
  
```csharp  
new SendMail  
{
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a><span data-ttu-id="34b68-188">Kurulum Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="34b68-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="34b68-189">Bu örnek için bir SMTP sunucusuna erişim gereklidir.</span><span class="sxs-lookup"><span data-stu-id="34b68-189">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="34b68-190">Bir SMTP sunucusu ayarlama hakkında daha fazla bilgi için aşağıdaki bağlantılara bakın.</span><span class="sxs-lookup"><span data-stu-id="34b68-190">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- <span data-ttu-id="34b68-191">[SMTP Hizmetini Yapılandırma (IIS 6.0)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="34b68-191">[Configuring the SMTP Service (IIS 6.0)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span></span>  
  
- <span data-ttu-id="34b68-192">[IIS 7.0: SMTP E-Postayı Yapılandır](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="34b68-192">[IIS 7.0: Configure SMTP E-Mail](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span></span>  
  
- <span data-ttu-id="34b68-193">[SMTP Hizmeti Nasıl Yüklenir?](https://docs.microsoft.com/previous-versions/tn-archive/aa997480(v=exchg.65))</span><span class="sxs-lookup"><span data-stu-id="34b68-193">[How to Install the SMTP Service](https://docs.microsoft.com/previous-versions/tn-archive/aa997480(v=exchg.65))</span></span>  
  
 <span data-ttu-id="34b68-194">Üçüncü şahıslar tarafından sağlanan SMTP emülatörleri indirilebilir.</span><span class="sxs-lookup"><span data-stu-id="34b68-194">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="34b68-195">Bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="34b68-195">To run this sample</span></span>  
  
1. <span data-ttu-id="34b68-196">Visual Studio 2010'u kullanarak SendMail.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="34b68-196">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="34b68-197">Geçerli bir SMTP sunucusuna erişebildiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="34b68-197">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="34b68-198">Kurulum yönergelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="34b68-198">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="34b68-199">Programı sunucu adresinizle ve E-posta adreslerinize göre yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="34b68-199">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="34b68-200">Bu örneği doğru çalıştırmak için, Program.cs ve Sequence.xaml'daki SMTP sunucusunun E-posta adreslerinin değerini ve adresini yapılandırmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="34b68-200">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="34b68-201">Program posta gönderdiğinden, her iki konumda da adresi değiştirmeniz gerekir</span><span class="sxs-lookup"><span data-stu-id="34b68-201">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="34b68-202">Çözümü oluşturmak için CTRL+SHIFT+B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="34b68-202">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="34b68-203">Çözümü çalıştırmak için CTRL+F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="34b68-203">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="34b68-204">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="34b68-204">The samples may already be installed on your machine.</span></span> <span data-ttu-id="34b68-205">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="34b68-205">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="34b68-206">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="34b68-206">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="34b68-207">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="34b68-207">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
